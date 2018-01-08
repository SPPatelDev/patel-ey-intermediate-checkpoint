(function() {
	"use strict";

	angular
		.module("app.shared-components")
		.directive("chartData", chartData);

	function chartData() {
		var directive = {
			scope: {},
            restrict: "E",
			controller: chartDataController,
			controllerAs: "vm",
			bindToController: true,
			templateUrl: "/chart-data/chart-data.directive.html",
		};
	
		return directive;
	}

	ChartDataController.$inject = ["chartDataService"];

	function ChartDataController(chartDataService) {
        var vm = this;
        
        activate();

        function activate() {
            
        }

        function getListItems() {
            listName = 'List Name';
            query = {
                select: "columnA, columnB",
                expand: 'columnB/ID, columnB/Title'
            };

            return chartDataService.getListItems(listName, query).then(function(items) {
                vm.items = items;
            });
        } 

        function formatItems(items) {
            // code here
        } 

	}
})();