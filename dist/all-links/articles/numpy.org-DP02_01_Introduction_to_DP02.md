NumPy -
Install
Documentation
Learn
Community
About Us
News
ContributeEnglishPortuguês
日本語 (Japanese)NumPy
The fundamental package for scientific computing with PythonLatest release: NumPy 2.0. View all releasesNumPy 2.0 released!2024-06-17Powerful N-dimensional arraysFast and versatile, the NumPy vectorization, indexing, and broadcasting concepts are the de-facto standards of array computing today.Numerical computing toolsNumPy offers comprehensive mathematical functions, random number generators, linear algebra routines, Fourier transforms, and more.Open sourceDistributed under a liberal BSD license, NumPy is developed and maintained publicly on GitHub by a vibrant, responsive, and diverse community.InteroperableNumPy supports a wide range of hardware and computing platforms, and plays well with distributed, GPU, and sparse array libraries.PerformantThe core of NumPy is well-optimized C code. Enjoy the flexibility of Python with the speed of compiled code.Easy to useNumPy’s high level syntax makes it accessible and productive for programmers from any background or experience level.Try NumPyUse the interactive shell to try NumPy in the browser"""
To try the examples in the browser:
1. Type code in the input cell and press
Shift + Enter to execute
2. Or copy paste the code, and click on
the "Run" button in the toolbar
"""
# The standard way to import NumPy:
import numpy as np
# Create a 2-D array, set every second element in
# some rows and find max per row:
x = np.arange(15, dtype=np.int64).reshape(3, 5)
x[1:, ::2] = -99
x
# array([[
0,
1,
2,
3,
4],
#
[-99,
6, -99,
8, -99],
#
[-99,
11, -99,
13, -99]])
x.max(axis=1)
# array([ 4,
8, 13])
# Generate normally distributed random numbers:
rng = np.random.default_rng()
samples = rng.normal(size=2500)
samplesECOSYSTEM
Scientific Domains
Array Libraries
Data Science
Machine Learning
VisualizationNearly every scientist working in Python draws on the power of NumPy.NumPy brings the computational power of languages like C and Fortran to Python, a language much easier to learn and use. With this power comes simplicity: a solution in NumPy is often clear and elegant.Quantum ComputingQuTiPPyQuilQiskitPennyLaneStatistical ComputingPandasstatsmodelsXarraySeabornSignal ProcessingSciPyPyWaveletspython-controlHyperSpyImage ProcessingScikit-imageOpenCVMahotasGraphs and NetworksNetworkXgraph-tooligraphPyGSPAstronomyAstroPySunPySpacePyCognitive PsychologyPsychoPyBioinformaticsBioPythonScikit-BioPyEnsemblETEBayesian InferencePyStanPyMC3ArviZemceeMathematical AnalysisSciPySymPycvxpyFEniCSChemistryCanteraMDAnalysisRDKitPyBaMMGeosciencePangeoSimpegObsPyFatiando a TerraGeographic ProcessingShapelyGeoPandasFoliumArchitecture & EngineeringCOMPASCity Energy AnalystSverchokNumPy's API is the starting point when libraries are written to exploit innovative hardware, create specialized array types, or add capabilities beyond what NumPy provides.Array LibraryCapabilities & Application areasDaskDistributed arrays and advanced parallelism for analytics, enabling performance at scale.CuPyNumPy-compatible array library for GPU-accelerated computing with Python.JAXComposable transformations of NumPy programs: differentiate, vectorize, just-in-time compilation to GPU/TPU.XarrayLabeled, indexed multi-dimensional arrays for advanced analytics and visualization.SparseNumPy-compatible sparse array library that integrates with Dask and SciPy's sparse linear algebra.PyTorchDeep learning framework that accelerates the path from research prototyping to production deployment.TensorFlowAn end-to-end platform for machine learning to easily build and deploy ML powered applications.ArrowA cross-language development platform for columnar in-memory data and analytics.xtensorMulti-dimensional arrays with broadcasting and lazy computing for numerical analysis.Awkward ArrayManipulate JSON-like data with NumPy-like idioms.uarrayPython backend system that decouples API from implementation; unumpy provides a NumPy API.tensorlyTensor learning, algebra and backends to seamlessly use NumPy, PyTorch, TensorFlow or CuPy.NumPy lies at the core of a rich ecosystem of data science libraries. A typical exploratory data science workflow might look like:Extract, Transform, Load: Pandas, Intake, PyJanitorExploratory analysis: Jupyter, Seaborn, Matplotlib, AltairModel and evaluate: scikit-learn, statsmodels, PyMC3, spaCyReport in a dashboard: Dash, Panel, VoilaFor high data volumes, Dask and Ray are designed to scale. Stable deployments rely on data versioning (DVC), experiment tracking (MLFlow), and workflow automation (Airflow, Dagster and Prefect).Source: Google AI BlogNumPy forms the basis of powerful machine learning libraries like scikit-learn and SciPy. As machine learning grows, so does the list of libraries built on NumPy. TensorFlow’s deep learning capabilities have broad applications — among them speech and image recognition, text-based applications, time-series analysis, and video detection. PyTorch, another deep learning library, is popular among researchers in computer vision and natural language processing.Statistical techniques called ensemble methods such as binning, bagging, stacking, and boosting are among the ML algorithms implemented by tools such as XGBoost, LightGBM, and CatBoost — one of the fastest inference engines. Yellowbrick and Eli5 offer machine learning visualizations.NumPy is an essential component in the burgeoning Python visualization landscape, which includes Matplotlib, Seaborn, Plotly, Altair, Bokeh, Holoviz, Vispy, Napari, and PyVista, to name a few.NumPy’s accelerated processing of large arrays allows researchers to visualize datasets far larger than native Python could handle.CASE STUDIESFirst Image of a Black HoleHow NumPy, together with libraries like SciPy and Matplotlib that depend on NumPy, enabled the Event Horizon Telescope to produce the first ever image of a black holeDetection of Gravitational WavesIn 1916, Albert Einstein predicted gravitational waves; 100 years later their existence was confirmed by LIGO scientists using NumPy.Sports AnalyticsCricket Analytics is changing the game by improving player and team performance through statistical modelling and predictive analytics. NumPy enables many of these analyses.Pose Estimation using deep learningDeepLabCut uses NumPy for accelerating scientific studies that involve observing animal behavior for better understanding of motor control, across species and timescales.InstallDocumentationLearnCiting NumpyRoadmapAbout usCommunityUser surveysContributeCode of conductGet helpTerms of usePrivacyPress kitSign up for the latest NumPy news, resources, and morePress EnterThank you! 🎉
© 2024 NumPy team. All rights reserved.