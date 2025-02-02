# Rxlize Angular Lifecycle Hooks

The Angular component lifecycle hooks is declare as callback (component methods) which not in observable form, it is hard to combine component lifecycle hooks in rxjs flow.

Below show how rxlize help developer to turn component hooks into observable.

### Example

```ts
@Component({...})
export class FooComponent {
  readonly rxHooks = rxNgHooks(this, 'ngOnChanges', 'ngOnDestroy');

  readonly userIdCtrl = new FormControl(1);

  constructor(private readonly router: Router) {
    // for those who unable to handle unsubscribe with async pipe in template
    // don't need to declare OnDestory hooks and Subject everytime by ourself
    this.userIdCtrl.valueChanges
      .pipe(takeUntil(this.rxNgHooks.ngOnDestroy))
      .subscribe(id => this.router.navigate(['/user', id]));

    // hooks with argument? no problem
    this.rxNgHooks.ngOnChanges.subscribe(changes => {
      // do something with SimpleChanges here
    });
  }
}
```
