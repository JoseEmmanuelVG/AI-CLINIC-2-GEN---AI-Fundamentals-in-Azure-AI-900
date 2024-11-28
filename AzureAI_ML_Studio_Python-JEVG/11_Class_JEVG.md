# Azure AI | Machine Learning Studio (Python - Process)

## Step 1: Create a Machine Learning Resource

To begin, we need to create a Machine Learning resource in the [Azure portal](https://azure.microsoft.com/products/machine-learning?wt.mc_id=studentamb_373747). You can refer to the notes on how to create it or reuse the resource created during **Class 2 - Introduction to Machine Learning Practice** in this repository: [Introduction - Practice of ML](https://github.com/JoseEmmanuelVG/AI-CLINIC-2-GEN---AI-Fundamentals-in-Azure-AI-900/blob/main/Intro-Study_of_ML-JEVG/2_Class_JEVG.md).

![Azure Portal Resource Creation](image.png)

Once the workspace has been created, you can configure a compute instance to execute your Python program:

![Compute Instance Configuration](image-1.png)

## Step 2: Introduction to Azure Machine Learning Compute Instances

Azure Machine Learning Studio provides preconfigured CPU or GPU instances for running Python notebooks, R scripts, or other Machine Learning workflows. These compute instances come with popular tools like JupyterLab, Jupyter, RStudio, ML packages, deep learning frameworks, and GPU drivers pre-installed.

![Compute Instance Options](image-2.png)

> **Note**: After completing your exercise, **ensure to stop the compute instance** to avoid unnecessary resource consumption. 

![Stop Compute Instance](image-3.png)
![Compute Instance Management](image-4.png)

## Step 3: Access Notebooks in Machine Learning Studio

Once the compute instance is created, navigate to the **Notebooks** section within Azure Machine Learning Studio. Here, you can create a Jupyter notebook script (Python) to run on the previously configured compute instance.

![Notebook Creation - Step 1](image-5.png)
![Notebook Creation - Step 2](image-6.png)
![Notebook Editor](image-7.png)

## Step 4: First Data Analysis Exercise

With the Jupyter notebook set up, you can write your script to perform your first data analysis exercise using Azure AI Machine Learning Studio.

![Data Analysis Setup](image-8.png)

### Dataset

We will use the following dataset: [Credit Card Default](https://www.kaggle.com/code/ybifoundation/credit-card-default). Load the dataset into your notebook with the following command:

```python
default = pd.read_csv('https://github.com/ybifoundation/Dataset/raw/main/Credit%20Default.csv')
```

# My First Data Analysis in Azure AI

This notebook demonstrates a basic data analysis workflow using Azure AI Machine Learning Studio. The dataset used in this example is the [Credit Card Default Dataset](https://www.kaggle.com/code/ybifoundation/credit-card-default). Below is a step-by-step breakdown of the process, including code, visualizations, and insights.

---

<div class="markdown prose w-full break-words dark:prose-invert light"><p>Here is the documentation Code</p><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">markdown</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-markdown"><span class="hljs-section"># My First Data Analysis in Azure AI</span>

This notebook demonstrates a basic data analysis workflow using Azure AI Machine Learning Studio. The dataset used in this example is the [<span class="hljs-string">Credit Card Default Dataset</span>](<span class="hljs-link">https://www.kaggle.com/code/ybifoundation/credit-card-default</span>). Below is a step-by-step breakdown of the process, including code, visualizations, and insights.

---

<span class="hljs-section">## STEP 1: Install Required Libraries and Load Dataset</span>

<span class="hljs-section">### Code:</span>
<span class="hljs-code">```python
%pip install seaborn

# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
dataset = pd.read_csv('https://github.com/ybifoundation/Dataset/raw/main/Credit%20Default.csv')

# Display the first few rows of the dataset
dataset.head()
</span></code></div></div></pre><h3>Explanation:</h3><ul><li>The dataset contains information on income, age, loan amounts, loan-to-income ratios, and default status (target variable).</li><li>The <code>.head()</code> method provides a quick preview of the first five rows.</li></ul><p><strong>Dataset Sample:</strong></p><table><thead><tr><th>Income</th><th>Age</th><th>Loan</th><th>Loan to Income</th><th>Default</th></tr></thead><tbody><tr><td>66155.92510</td><td>59.017015</td><td>8106.532131</td><td>0.122537</td><td>0</td></tr><tr><td>34415.15397</td><td>48.117153</td><td>6564.745018</td><td>0.190752</td><td>0</td></tr><tr><td>57317.17006</td><td>63.108049</td><td>8020.953296</td><td>0.139940</td><td>0</td></tr><tr><td>42709.53420</td><td>45.751972</td><td>6103.642260</td><td>0.142911</td><td>0</td></tr><tr><td>66952.68885</td><td>18.584336</td><td>8770.099235</td><td>0.130990</td><td>1</td></tr></tbody></table><hr><h2>STEP 2: Exploratory Data Analysis (EDA)</h2><h3>Code:</h3><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">python</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-python"><span class="hljs-comment"># General information about the dataset</span>
dataset.info()
</code></div></div></pre><h3>Output:</h3><p>The dataset consists of 2000 rows and 5 columns, with no missing values. The data types are:</p><ul><li><strong>float64</strong> for numerical columns like <code>Income</code>, <code>Age</code>, <code>Loan</code>, and <code>Loan to Income</code>.</li><li><strong>int64</strong> for the binary target variable <code>Default</code>.</li></ul><hr><h3>Target Variable Distribution</h3><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">python</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-python"><span class="hljs-comment"># Count occurrences of the target variable (Default)</span>
counter = dataset[<span class="hljs-string">"Default"</span>].value_counts()

<span class="hljs-comment"># Visualize the distribution of the target variable</span>
sns.countplot(x=<span class="hljs-string">"Default"</span>, data=dataset)
plt.title(<span class="hljs-string">"Targets Distribution"</span>)
plt.show()
</code></div></div></pre><h3>Visualization:</h3><p><img alt="Targets Distribution" src="image-9.png"></p><h3>Insights:</h3><ul><li>The target variable <code>Default</code> is imbalanced, with the majority of entries marked as <code>0</code> (no default). This imbalance may impact the model's performance and should be addressed during model training.</li></ul><hr><h3>Feature Analysis: Income Distribution</h3><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">python</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-python"><span class="hljs-comment"># Analyze the distribution of income</span>
plt.hist(dataset[<span class="hljs-string">'Income'</span>], bins=<span class="hljs-number">50</span>)
plt.title(<span class="hljs-string">"Income Distribution"</span>)
plt.ylabel(<span class="hljs-string">"Quantity"</span>)
plt.xlabel(<span class="hljs-string">"Frequency"</span>)
plt.show()
</code></div></div></pre><h3>Visualization:</h3><p><img alt="Income Distribution" src="image-10.png"></p><h3>Insights:</h3><ul><li>The <code>Income</code> feature appears to be right-skewed, with a majority of observations concentrated in the lower income ranges. Outliers with significantly higher incomes are present.</li></ul><hr><h3>Feature Analysis: Loan Distribution</h3><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">python</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-python"><span class="hljs-comment"># Analyze the distribution of loan amounts</span>
plt.hist(dataset[<span class="hljs-string">'Loan'</span>], bins=<span class="hljs-number">50</span>)
plt.title(<span class="hljs-string">"Loan Distribution"</span>)
plt.ylabel(<span class="hljs-string">"Quantity"</span>)
plt.xlabel(<span class="hljs-string">"Frequency"</span>)
plt.show()
</code></div></div></pre><h3>Visualization:</h3><p><img alt="Loan Distribution" src="image-11.png"></p><h3>Insights:</h3><ul><li>The <code>Loan</code> feature also appears right-skewed, with most loans in the lower range and fewer larger loans.</li></ul><hr><h3>Correlation Analysis</h3><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">python</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-python"><span class="hljs-comment"># Compute the correlation matrix</span>
corr_matrix = dataset.corr()

<span class="hljs-comment"># Visualize the correlation matrix</span>
plt.figure(figsize=(<span class="hljs-number">20</span>, <span class="hljs-number">15</span>))
sns.heatmap(corr_matrix, 
            annot=<span class="hljs-literal">True</span>, 
            cmap=<span class="hljs-string">'coolwarm'</span>)
plt.title(<span class="hljs-string">"Correlation matrix of the variables"</span>)
plt.show()
</code></div></div></pre><h3>Visualization:</h3><p><img alt="Correlation Matrix" src="image-12.png"></p><h3>Insights:</h3><ul><li><strong>Strong correlations</strong>:<ul><li><code>Loan to Income</code> is highly correlated with <code>Loan</code> and negatively correlated with <code>Income</code>, as expected.</li></ul></li><li><strong>Weak correlation with <code>Default</code></strong>:<ul><li>None of the features show a very strong correlation with the target variable <code>Default</code>. Feature engineering or more complex models may be required to improve predictions.</li></ul></li></ul><hr><h2>Summary of the Workflow:</h2><ol><li>Loaded and inspected the dataset.</li><li>Performed exploratory data analysis (EDA) to understand the distribution of target and feature variables.</li><li>Visualized key features and identified correlations using histograms and heatmaps.</li></ol><p>This analysis provides a solid foundation for preprocessing the data and building predictive models using Azure Machine Learning. For more details on using Azure ML, refer to the <a rel="noopener" target="_new" href="https://learn.microsoft.com/azure/machine-learning/?wt.mc_id=academic&amp;wt.mc_id=studentamb_373747" style="--streaming-animation-state: var(--batch-play-state-1); --animation-rate: var(--batch-play-rate-1);"><span style="--animation-count: 7; --streaming-animation-state: var(--batch-play-state-2);">Azure</span><span style="--animation-count: 8; --streaming-animation-state: var(--batch-play-state-2);"> Machine</span><span style="--animation-count: 9; --streaming-animation-state: var(--batch-play-state-2);"> Learning</span><span style="--animation-count: 10; --streaming-animation-state: var(--batch-play-state-2);"> documentation</span></a>.</p><pre class="!overflow-visible"><div class="contain-inline-size rounded-md border-[0.5px] border-token-border-medium relative bg-token-sidebar-surface-primary dark:bg-gray-950"><div class="flex items-center text-token-text-secondary px-4 py-2 text-xs font-sans justify-between rounded-t-md h-9 bg-token-sidebar-surface-primary dark:bg-token-main-surface-secondary select-none">css</div><div class="sticky top-9 md:top-[5.75rem]"><div class="absolute bottom-0 right-2 flex h-9 items-center"><div class="flex items-center rounded bg-token-sidebar-surface-primary px-2 font-sans text-xs text-token-text-secondary dark:bg-token-main-surface-secondary"><span class="" data-state="closed"><button class="flex gap-1 items-center select-none py-1"><svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="icon-sm"><path fill-rule="evenodd" clip-rule="evenodd" d="M7 5C7 3.34315 8.34315 2 10 2H19C20.6569 2 22 3.34315 22 5V14C22 15.6569 20.6569 17 19 17H17V19C17 20.6569 15.6569 22 14 22H5C3.34315 22 2 20.6569 2 19V10C2 8.34315 3.34315 7 5 7H7V5ZM9 7H14C15.6569 7 17 8.34315 17 10V15H19C19.5523 15 20 14.5523 20 14V5C20 4.44772 19.5523 4 19 4H10C9.44772 4 9 4.44772 9 5V7ZM5 9C4.44772 9 4 9.44772 4 10V19C4 19.5523 4.44772 20 5 20H14C14.5523 20 15 19.5523 15 19V10C15 9.44772 14.5523 9 14 9H5Z" fill="currentColor"></path></svg>Copiar código</button></span></div></div></div><div class="overflow-y-auto p-4" dir="ltr"><code class="!whitespace-pre hljs language-css">
Este documento Markdown incluye descripciones completas <span class="hljs-selector-tag">del</span> código, visualizaciones y su interpretación, utilizando un lenguaje técnico formal. También incluye tu Contributor ID en los enlaces relevantes. Avísame si necesitas algo más. 😊
</code></div></div></pre></div>



-----------






















































> **Contributor ID Notice**: This content includes links that track participation using my Microsoft Student Ambassador Contributor ID. By clicking these links, you contribute to engagement metrics that support the Ambassador program.




<details>
  <summary>🌟 Did you find any repository useful?</summary>
  If any project has been helpful to you, consider giving it a ⭐ star in the repository and follow my GitHub account to stay tuned for future updates! 🚀

  In addition, I am always open to suggestions, recommendations or collaborations. Feel free to [get in touch](https://www.linkedin.com/in/vazquez-galan-jose-emmanuel-664968221) if you have any questions or ideas for improving this project. I'm excited for your feedback and contributions.

  Thank you for your interest and support! 😊
</details>


<p align="center">
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
</p>