(function() {
	"use strict";

	angular
		.module("app.shared-services")
		.factory("chartDataService", chartDataService);

	chartDataService.$inject = ["restService"];

	function chartDataService(restService) {

		var service = {
            getListItems: getListItems
		};

		return service;

		function getListItems(listTitle, queryParams) {
            return restService.getListItems(listTitle, queryParams)
            .then(getListItemsComplete); 

            function getListItemsComplete(items) {
                return items;
            }
		}

    }
    
})();
