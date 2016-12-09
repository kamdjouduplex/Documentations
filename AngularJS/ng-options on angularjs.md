## ng-options rendering in the view

### what is ng-options
ng-options allowed us to repeat the value in the option tag of the html select tag


### example code
```javascript
<select name="" ng-model="search.brand" ng-options="b.id as b.nom for b in brands" class="form-control">
    <option value="">brand</option>
</select>
```

