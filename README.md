# Angular- with Odata service

#### Start-up Angular Js APP as follows 

    <!doctype html>
    <html ng-app="myApp">
    	<head>
    		<script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>
    	</head>
    	<body>
        <div ng-controller="customersCtrl">
      		 
      	</div>
        <script>
      		var app = angular.module('myApp', []);
      		app.controller('customersCtrl', function() {
      		 //do something 
      		});
    		</script>
    	</body>
    </html>

1. Add ng-app="myApp" in **html** tag
2. Use "http://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js" on **head** 
3. Add ng-controller="customersCtrl" to **div** tag(where we want get data from the JS script)
4. In **script** create a Angular Js app "var app = angular.module('myApp', []);"
5. write the actual code in "app.controller"

We will use **Northwind** Odata service to get data - [Link](http://services.odata.org/V2/Northwind/Northwind.svc/Customers)

In Controller file we will use **AngularJS $http**, The AngularJS $http service makes a request to the server, and returns a response.

    app.controller('customersCtrl', function($scope, $http) {
      $http.get("http://services.odata.org/V2/Northwind/Northwind.svc/Customers?$format=json").then(function (response) {
        $scope.myData = response.data.d.results;
      });
    });

Now all data from the service will be added to "myData"

#### Create Table in HTML as- 

    <table>
      <tr>
      	<th>Customer ID</th>
      	<th>Customer Name</th>
      	<th>Company Name</th>
      </tr>
      <tr ng-repeat="x in myData">
      	<td>{{x.CustomerID}}</td>
      	<td>{{x.ContactName}}</td>
      	<td>{{x.CompanyName}}</td>
      </tr>
    </table>

In `<tr>` row tag we use "ng-repeat"(as for loop) to get data from "myData" to "x" and put it to `<td>`.

And it's done we have the Simple Angular Js App to get data from a server and show in HTML table.

Note - I am using **Bootstrap** for UI. Please see the Index.html for the full code. working example - [Link](http://chandankalita.com/demo/FirstAjs/)
