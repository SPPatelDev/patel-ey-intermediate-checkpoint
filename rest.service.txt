(function() {
	"use strict";

	angular
		.module("app.shared-services")
		.factory("restService", restService);

	restService.$inject = ["$http", "$q"];

	function restService($http, $q) {

		var service = {
            getListItems: getListItems
		};

		return service;

		function getListItems(listTitle, queryParams) {
            var dfd = $q.defer();
            $http.defaults.headers.post['X-HTTP-Method'] = "";
            var restUrl = "../_api/web/lists/getbytitle('" + listTitle + "')/items" + queryParams;
            $http.get(restUrl).success(function(data) {
                dfd.resolve(data.d.results);
            }).error(function(data) {
                dfd.reject("error, cannot get items"); 
            });
            return dfd.promise;
		}

	}
})();
