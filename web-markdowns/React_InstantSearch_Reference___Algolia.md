React InstantSearch Reference | Algolia                      

[](/doc/)

Close

Guides

Learn how Algolia works and how you can use it to create search and discovery experiences.

[

Home



](/doc/)[

Getting started



](/doc/guides/getting-started/what-is-algolia/)[

Sending and managing data



](/doc/guides/sending-and-managing-data/prepare-your-data/)[

Managing results



](/doc/guides/managing-results/relevance-overview/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/android/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/angular/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/flutter/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/ios/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/js/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/react/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/vue/)

[

Sending events



](/doc/guides/sending-events/getting-started/)[

Search analytics



](/doc/guides/search-analytics/overview/)[

Personalization



](/doc/guides/personalization/ai-personalization/what-is-ai-personalization/)[

A/B testing



](/doc/guides/ab-testing/what-is-ab-testing/)[

Algolia Recommend



](/doc/guides/algolia-recommend/overview/)[

Algolia AI



](/doc/guides/algolia-ai/dynamic-synonym-suggestions/)[

Going to production



](/doc/guides/going-to-production/preparing-your-project/)[

Scaling



](/doc/guides/scaling/servers-clusters/)[

Security



](/doc/guides/security/api-keys/)[

Solutions



](/doc/guides/solutions/ecommerce/search/)

API clients

[

PHP



](/doc/api-client/getting-started/install/php/)[

Ruby



](/doc/api-client/getting-started/install/ruby/)[

JavaScript



](/doc/api-client/getting-started/install/javascript/)[

Python



](/doc/api-client/getting-started/install/python/)[

Swift



](/doc/api-client/getting-started/install/swift/)[

Kotlin



](/doc/api-client/getting-started/install/kotlin/)[

.NET



](/doc/api-client/getting-started/install/csharp/)[

Java



](/doc/api-client/getting-started/install/java/)[

Go



](/doc/api-client/getting-started/install/go/)[

Scala



](/doc/api-client/getting-started/install/scala/)

UI libraries

[

InstantSearch.js



](/doc/api-reference/widgets/js/)[

React InstantSearch



](/doc/api-reference/widgets/react/)[

Vue InstantSearch



](/doc/api-reference/widgets/vue/)[

Angular InstantSearch



](/doc/api-reference/widgets/angular/)[

InstantSearch iOS



](/doc/api-reference/widgets/ios/)[

InstantSearch Android



](/doc/api-reference/widgets/android/)[

Algolia for Flutter



](/doc/guides/building-search-ui/widgets/showcase/flutter/)

[

Autocomplete



](/doc/ui-libraries/autocomplete/introduction/what-is-autocomplete/)

API parameters

[

Index settings and search parameters



](/doc/api-reference/api-parameters/)

REST API

[

A full reference of API endpoints



](/doc/api-reference/rest-api/)

Crawler

[

Configuration API



](/doc/tools/crawler/apis/configuration/)

Integrations

Speed up your implementation with Algolia's integrations and tools.

Web frameworks

[

Rails



](/doc/framework-integration/rails/getting-started/setup/)[

Symfony



](/doc/framework-integration/symfony/getting-started/algolia-searchbundle/)[

Django



](/doc/framework-integration/django/setup/)[

Laravel



](/doc/framework-integration/laravel/getting-started/introduction-to-scout-extended/)

Tools

[

Crawler



](/doc/tools/crawler/getting-started/overview/)[

CLI



](/doc/tools/cli/get-started/overview/)

Platforms

[

Magento 2



](/doc/integration/magento-2/getting-started/quick-start/)[

Shopify



](/doc/integration/shopify/getting-started/quick-start/)[

commercetools



](/doc/integration/commercetools/getting-started/installation)[

BigCommerce



](/doc/integration/bigcommerce/get-started/installation)[

Salesforce Commerce Cloud B2C



](/doc/integration/salesforce-commerce-cloud-b2c/getting-started/introduction/)[

Netlify



](/doc/tools/crawler/netlify-plugin/quick-start/)[

Zendesk



](/doc/integration/zendesk/get-started/)

UI libraries / React InstantSearch

React InstantSearch
===================

[Edit this page](https://github.com/algolia/doc/edit/master/source/doc/api-reference/widgets.html.haml) [A Edit this page](https://atwood-editor.algolia.com/?gh-paths=source/doc/api-reference/widgets.html.haml "Edit this page")

**This is the React InstantSearch v7 documentation.** React InstantSearch v7 is the latest version of React InstantSearch and the stable version of React InstantSearch Hooks.  
  
If you were using React InstantSearch v6, you can [upgrade to v7](/doc/guides/building-search-ui/upgrade-guides/react/#migrate-from-react-instantsearch-v6-to-react-instantsearch-v7).  
  
If you were using React InstantSearch Hooks, you can still use the React InstantSearch v7 documentation, but you should check the [upgrade guide](/doc/guides/building-search-ui/upgrade-guides/react/#migrate-from-react-instantsearch-hooks-to-react-instantsearch-v7) for necessary changes.  
  
If you want to keep using React InstantSearch v6, you can find the [archived documentation](/doc/deprecated/instantsearch/react/v6/api-reference/instantsearch/).

React InstantSearch is an open-source, UI library for React that lets you quickly build a search interface in your frontend application.

To get started, install React InstantSearch and its dependencies.

Shell

Copy

    1
    2
    3
    yarn add algoliasearch react-instantsearch
    # or
    npm install algoliasearch react-instantsearch
    

Then, import the library in your React application.

JSX

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    import algoliasearch from 'algoliasearch/lite';
    import { InstantSearch } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="YourIndexName">
          {/* ... */}
        </InstantSearch>
      );
    }
    

**You're ready to use React InstantSearch.** Check out all available widgets and Hooks below.

Guides [Building Search UI](/doc/guides/building-search-ui/what-is-instantsearch/react/)

Basics
------

[<InstantSearch>](/doc/api-reference/widgets/instantsearch/react/)

The root provider component of all widgets and Hooks.

[useInstantSearch()](/doc/api-reference/widgets/use-instantsearch/react/)

React Hook to access the InstantSearch API.

[<Index>](/doc/api-reference/widgets/index-widget/react/)

The provider component for an Algolia index.

[<SearchBox>](/doc/api-reference/widgets/search-box/react/)

A widget to display a search box.

[<Configure>](/doc/api-reference/widgets/configure/react/)

A widget to forward search parameters to Algolia.

[useConfigureRelatedItems()](/doc/api-reference/widgets/configure-related-items/react/)

React Hook to use a configure related items connector.

[useAutocomplete()](/doc/api-reference/widgets/autocomplete/react/)

React Hook to use an Autocomplete connector.

[useVoiceSearch()](/doc/api-reference/widgets/voice-search/react/)

React Hook to use a voice search connector.

[insights](/doc/api-reference/widgets/insights/react/)

A middleware to help set the `userToken` for insights purposes, and send events from built-in and custom widgets.

[middleware](/doc/api-reference/widgets/middleware/react/)

With the middleware API, you can inject functionality into InstantSearch.js.

[renderState](/doc/api-reference/widgets/render-state/react/)

The `renderState` provides access to all the data to render the widgets, including the methods to refine the search.

[useConnector()](/doc/api-reference/widgets/connector/react/)

React Hook to use an InstantSearch connector.

Results
-------

[<Hits>](/doc/api-reference/widgets/hits/react/)

A widget to display a list of search results.

[<InfiniteHits>](/doc/api-reference/widgets/infinite-hits/react/)

A widget to display an infinite list of results.

[<Highlight>](/doc/api-reference/widgets/highlight/react/)

A widget to display highlighted attributes of a search result.

[<Snippet>](/doc/api-reference/widgets/snippet/react/)

A widget that displays attributes in your search results in a shorter form (a snippet).

Recommendations
---------------

[<FrequentlyBoughtTogether>](/doc/api-reference/widgets/frequently-bought-together/react/)

A widget to display a list of frequently bought together items.

[<RelatedProducts>](/doc/api-reference/widgets/related-products/react/)

A widget to display a list of related products and related content.

[<TrendingItems>](/doc/api-reference/widgets/trending-items/react/)

A widget to display a list of trending items.

[<TrendingFacets>](/doc/api-reference/widgets/trending-facets/react/)

A widget to display a list of [Trending Facets](/doc/guides/algolia-recommend/overview/#trending-items-and-trending-facet-values).

[<LookingSimilar>](/doc/api-reference/widgets/looking-similar/react/)

A widget to display a list of visually similar products.

Refinements
-----------

[<RefinementList>](/doc/api-reference/widgets/refinement-list/react/)

A widget to display multi-select facets.

[<ColorRefinementList>](/doc/api-reference/widgets/color-refinement-list/react/)

A widget that filters results based on color facet values. It helps users quickly visualize the kind of color that products have.

[<DynamicWidgets>](/doc/api-reference/widgets/dynamic-facets/react/)

A widget to conditionally render other widgets based on the index settings.

[<HierarchicalMenu>](/doc/api-reference/widgets/hierarchical-menu/react/)

A widget to create a navigation menu based on a hierarchy of facet attributes. It’s commonly used for categories with subcategories.

[useRange()](/doc/api-reference/widgets/range-slider/react/)

React Hook to filter search results within a numeric range.

[<Menu>](/doc/api-reference/widgets/menu/react/)

A widget to display a menu to let users choose a single value.

[<CurrentRefinements>](/doc/api-reference/widgets/current-refinements/react/)

A widget to display the list of active refinements in the search.

[<RangeInput>](/doc/api-reference/widgets/range-input/react/)

A widget to select a numerical range using minimum and maximum inputs.

[<MenuSelect>](/doc/api-reference/widgets/menu-select/react/)

A widget to use a menu select connector.

[<ToggleRefinement>](/doc/api-reference/widgets/toggle-refinement/react/)

A widget to provide an on/off filter.

[useNumericMenu()](/doc/api-reference/widgets/numeric-menu/react/)

React Hook that shows a list of numeric filters that are pre-configured when creating the widget.

[useRatingMenu()](/doc/api-reference/widgets/rating-menu/react/)

React Hook to use a rating menu connector.

[<ClearRefinements>](/doc/api-reference/widgets/clear-refinements/react/)

A widget to reset the active refinements of the search.

Pagination
----------

[<Pagination>](/doc/api-reference/widgets/pagination/react/)

A widget to display a pagination to browse pages.

[<HitsPerPage>](/doc/api-reference/widgets/hits-per-page/react/)

A widget to display a menu of options to change the number of results per page.

Metadata
--------

[<Breadcrumb>](/doc/api-reference/widgets/breadcrumb/react/)

A widget to display navigation links to see where the current page is in relation to the facet’s hierarchy.

[<Stats>](/doc/api-reference/widgets/stats/react/)

A widget that displays the total number of matching hits and the time it took to get them (time spent in the Algolia server).

[<PoweredBy>](/doc/api-reference/widgets/powered-by/react/)

A widget to display the Algolia logo to redirect to the Algolia website.

[StateResults](/doc/api-reference/widgets/state-results/react/)

A widget for accessing the state and results of InstantSearch.

[<QueryRulesCustomData>](/doc/api-reference/widgets/query-rule-custom-data/react/)

A widget to display custom data from rules.

[<QueryRuleContext>](/doc/api-reference/widgets/query-rule-context/react/)

A widget to set Rule contexts without rendering anything.

[useQueryRules()](/doc/api-reference/widgets/query-rules/react/)

React Hook to set custom Rule contexts and display custom data from Rules.

Sorting
-------

[<SortBy>](/doc/api-reference/widgets/sort-by/react/)

A widget to sort by specified indices.

[useRelevantSort()](/doc/api-reference/widgets/relevant-sort/react/)

React Hook to use a relevant sort connector.

Geo Search
----------

[useGeoSearch()](/doc/api-reference/widgets/geo-search/react/)

A React Hook that displays search results on a Google Map.

Routing
-------

[simple](/doc/api-reference/widgets/simple-state-mapping/react/)

A state mapping used by default with [routing](/doc/api-reference/widgets/instantsearch/react/#widget-param-routing).

[history](/doc/api-reference/widgets/history-router/react/)

A router used by default with [routing](/doc/api-reference/widgets/instantsearch/react/#widget-param-routing).

[uiState](/doc/api-reference/widgets/ui-state/react/)

An object that represents the state of the search.

[createInstantSearchRouterNext()](/doc/api-reference/widgets/instantsearch-next-router/react/)

The function that creates a Next.js-compatible InstantSearch router to pass to [routing](/doc/api-reference/widgets/instantsearch/react/#widget-param-routing).

Server
------

[<InstantSearchSSRProvider>](/doc/api-reference/widgets/ssr-provider/react/)

The provider component that forwards the server state to [`<InstantSearch>`](/doc/api-reference/widgets/instantsearch/react/).

[getServerState()](/doc/api-reference/widgets/server-state/react/)

The function that retrieves the server state to pass to [`<InstantSearchSSRProvider>`](/doc/api-reference/widgets/ssr-provider/react/).

Did you find this page helpful?

Yes, I found this page helpful.

No, I didn't find this page helpful.

We appreciate your feedback! Please note that we can't respond.

If you have questions, please reach out to [the support team](https://www.algolia.com/support/?contact=).

Looks like there's an issue on our end. Please copy the message below and send it to [the support team](https://www.algolia.com/support/?contact=).

Submit

React InstantSearch v7

[

InstantSearch.js v4





](/doc/api-reference/widgets/js/)[

React InstantSearch v7





](/doc/api-reference/widgets/react/)[

Vue InstantSearch v4





](/doc/api-reference/widgets/vue/)[

Angular InstantSearch v4





](/doc/api-reference/widgets/angular/)[

InstantSearch iOS v7





](/doc/api-reference/widgets/ios/)[

InstantSearch Android v3





](/doc/api-reference/widgets/android/)[

Algolia for Flutter v1





](/doc/api-reference/widgets/flutter/)

[Need help?](https://www.algolia.com/support/)

React InstantSearch v7

[

InstantSearch.js v4





](/doc/api-reference/widgets/js/)[

React InstantSearch v7





](/doc/api-reference/widgets/react/)[

Vue InstantSearch v4





](/doc/api-reference/widgets/vue/)[

Angular InstantSearch v4





](/doc/api-reference/widgets/angular/)[

InstantSearch iOS v7





](/doc/api-reference/widgets/ios/)[

InstantSearch Android v3





](/doc/api-reference/widgets/android/)[

Algolia for Flutter v1





](/doc/api-reference/widgets/flutter/)