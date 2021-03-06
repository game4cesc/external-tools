AtomSpace Viewer - README
=========================

Introduction
------------
The AtomSpace Viewer is a tool that allows you to dynamically visualize the atoms from a running CogServer instance. See the help file (av_help.html) for instructions on how to configure and use the Viewer. You'll first need to set up the [REST API](http://wiki.opencog.org/w/Web_interface) for your OpenCog build.

To run the Viewer, download the entire AtomViewer directory tree, including all sub-folders. Then open atom_viewer.html (from the WebContent folder) in your web browser. The AtomSpace Viewer can be run as a standalone app in the brower, it does not need to be hosted on a web server. There are no external dependencies either, but you should use the latest version of a modern web browser that supports HTML5 and CORS (e.g. Chrome, Firefox, Internet Explorer, etc.).

Development
-----------
The AtomSpace Visualizer is written entirely in JavaScript and HTML5, and was designed so that it can run standalone in just the web browser, or easily be added to a more comprehensive "workbench" type web application later. It uses the [Dojo Toolkit](http://dojotoolkit.org/) for the user interface, and the [JavaScript InfoVis Toolkit](http://philogb.github.io/jit/index.html) for graphing.

The project is configured for Eclipse (Kepler) web development. The [Aptana Studio 3](http://www.aptana.com/) plugin for Eclipse is recommended (but not required). Chrome and Firefox are the recommended browers for testing and debugging.

TODO (High Priority)
--------------------
* Implement the atom edit feature (including delete function).
* Implement auto-update feature. Ideally this should use the ZMQ atom change notification system (http://wiki.opencog.org/w/AtomSpace_Event_Publisher), but there are some performance issues with that at present (see https://github.com/opencog/opencog/pull/447). Could use a timer and polling for the short-term instead.
* For search/filter results, include option to also show the other atoms that are within N links of the search results.
* Dynamically popluate the atom type combobox. It should get these from the CogServer at run time. Requires change to REST API.

TODO (Medium Priority)
----------------------
* Implement the Table and Scheme views (for Scheme, need addition to the REST API to return equivalent of the "list -a" console command)  
* Beef up error handling (e.g. 404 not found for atom search by handle, etc.)
* Use gradient or similar method for node colors, based on importance or other configurable attribute.
* Thin out the Dojo libraries and CSS to remove unused parts, compress files.

TODO (Nice to Have)
-------------------
* Find links with a given atom as target.
* Pattern matching, e.g. ﬁnd atoms satisfying some predicate.
* Neighborhood search, e.g. ﬁnd atoms that are within some radius of a given centroid atom.
* Find atoms by TruthValue criteria.
* Find atoms based on some temporal or spatial association.
* Add more views (e.g. 3d graph, pinpoint graph (>350 atoms), patterns, etc.)
* Add cancel button to stop atom retrieval.
* Implement the Analysis feature (atom stats, etc.)

Known Bugs
----------
* On Firefox browser, the resize event is not firing, so graph doesn't resize automatically (works on other browsers).
* On Chrome browser, dragging graph nodes gets confused with drag-selection, causing painting issues (not a problem on other browsers).
* JIT graph sometimes draws nodes off edge of canvas.
* JSONP error function is never called by Dojo.
* Asynch progress is not incremental on large datasets, probably need to add paging in the REST API.
* When a search result contains only Link atoms, the JIT graph draws extraneous nodes.
 
