'use strict';

angular.module('tutorialApp', ['ngRoute'])
  .factory('Cart', function() {
 
    var articleList = [];
    return {
      
      getArticle: function() {
	return articleList;
      },
      addArticle: function(article) {
       
	for(var i =0; i < articleList.length; i++){
		if(articleList[i].id === article.id){
		   articleList[i].count ++;
		   return;
		}
	}
	var art = {id : article.id, name : article.name, price : article.price, count : 1};
	articleList.push(art);
        
      },
      removeArticle : function(id) {
	for (var i =0; i < articleList.length; i++)
	   if (articleList[i].id === id) {
	      articleList[i].count --;
	      if(articleList[i].count<=0){
		articleList.splice(i,1);
	      }
	      break;
	   }
      },
      getArticleCount : function() {
	var count = 0;
        for (var i =0; i < articleList.length; i++){
		count += articleList[i].count;
	}
	return count;
      },
      sum: function() {
	var count = 0;
        for (var i =0; i < articleList.length; i++){
		count += articleList[i].count * articleList[i].price;
	}
	return count;
      }
    };
  })
  .controller('ArticlesCtrl', function($scope, $http, Cart){
    $scope.cart = Cart;
    $http.get('articles.json').then(function(articlesResponse) {
      $scope.articles = articlesResponse.data;
    });
  })
  .controller('CartCtrl', function($scope, Cart){
    $scope.cart = Cart;
  });
