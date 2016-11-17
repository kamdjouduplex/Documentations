# $resource service in angularjs

to use the update method of the angularjs resource service,

### 1 - we need to create the service
 here is a sample service created in angularjs
`
 app.factory('MyService', 
	['$resource', 'API_URL','UserAPIParamsService', function ( $resource, API_URL, UserAPIParamsService) {
		var user_params = UserAPIParamsService.getUserParams();
		return $resource(
			API_URL + 'users/:id'+user_params,
			{id: '@_id'},
			{update: {method: 'PUT' /* this method issues a PUT request*/}},
			{query: {method: 'GET', isArray: true}},
			{stripTrailingSlashes: false }
		);
	}]
);
`


### 2 - We need a controller where we will call the Service
	here is a sample code too
`
app.controller('MyController', ['$scope', 'MyService', function($scope, MyService){
	
	$scope.update = function(){
		//here start my resource for updating the data
		var updatedData = $scope.formData  //all the data from the form is save here

		MyService.update({ id:id }, updatedData, function (response) {  //id here is the id of the element to update
          var data = response; //here response if the callback after sucessfully updated
        });
	}
}])
`