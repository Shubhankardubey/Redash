# Redash
It is a text file by which we can add a new visualization in redash.io

-------------------------------------------- To Add Visualization in Redash.io ---------------------------------------------------------
1. Make a index.js which whould contain the logics and implementation of the visualization with the help of d3.js
2. Make a .css file which would contain the styles script
3. NewVisualize.html which which contains the visualzation part in html
4. NewVisualize-editor.html which which contains the edit the visualzation part in html

We have to config the value ( ngModule.Config ) so that it can load the visualization provider with the rendering templates,
along with editing part, the logics part, the various options and methods etc.

In index.js part we have to register the new visualization with the visualzation provider so that it can be accessable from
the total visualizations list.

If we are making a new function and that function is being used directly by the module of the app we have to define in the 
ngModule.directive.

------------------------------------------------------ EXAMPLE ------------------------------------------------------------
#
export default function init(ngModule) { 				// INIT THE NGMODULE WITH DIRECTIVE AND CONFIG 
  ngModule.directive('cohortRenderer', cohortRenderer);
  ngModule.directive('cohortEditor', cohortEditor);

  ngModule.config((VisualizationProvider) => {
    const editTemplate = '<cohort-editor></cohort-editor>';

    VisualizationProvider.registerVisualization({			// PROVIDES THE TYPE, NAME, TEMPLATE of the new visualizations
      type: 'COHORT',
      name: 'Cohort',
      renderTemplate: '<cohort-renderer options="visualization.options" query-result="queryResult"></cohort-renderer>',
      editorTemplate: editTemplate,
      defaultOptions: DEFAULT_OPTIONS,
    });
  });
} 

init.init = true; 


At last we have to intialise the index.js with the true value so that it can load on the app load.

Note - This dashboard uses d3.js for render visualizations. To add a new visualiation we have to select the visualzation
from the d3.js, read their documentation how to add a new visualzation and thus from there using the above techniques we
can add new visualizations. Also if we know how to write visualzations code from the scratch write along with the above
techniques and initialise as stated above.

#What dashboard does after selecting the new visualizations?
Dashboard will render the new visualization as per the new name .  



