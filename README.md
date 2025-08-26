<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Risk & Decision Analysis Toolkit</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        .vertical-text {
            writing-mode: vertical-rl;
            transform: rotate(180deg);
        }
        .table-cell-level {
            padding: 0.75rem;
            text-align: center;
            font-weight: bold;
            color: white;
            border-radius: 0.375rem;
        }
        .risk-card {
            transition: border-color 0.3s ease-in-out;
        }
        /* Tab Styles */
        .tab-btn.active {
            border-color: #3b82f6;
            color: #3b82f6;
            background-color: #eff6ff;
        }
        .tab-content {
            display: none;
        }
        .tab-content.active {
            display: block;
        }
        /* Tornado Graph Styles */
        .tornado-bar {
            transition: width 0.3s ease-in-out;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <div class="container mx-auto p-4 sm:p-6 lg:p-8">
        <header class="text-center mb-8">
            <h1 class="text-3xl sm:text-4xl font-bold text-gray-900">Risk & Decision Analysis Toolkit</h1>
            <p class="mt-2 text-lg text-gray-600">A visual suite to assess, prioritize, and decide on complex project challenges.</p>
        </header>

        <main>
            <!-- Tabs Container -->
            <div class="bg-white rounded-xl shadow-lg">
                <!-- Tabs Navigation -->
                <div class="border-b border-gray-200">
                    <nav class="-mb-px flex space-x-4 p-4 overflow-x-auto" aria-label="Tabs">
                        <button class="tab-btn active whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm" data-tab="tab1">Matrix & Methodology</button>
                        <button class="tab-btn whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm text-gray-500 hover:text-gray-700 hover:border-gray-300" data-tab="tab6">Response Strategies</button>
                        <button class="tab-btn whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm text-gray-500 hover:text-gray-700 hover:border-gray-300" data-tab="tab2">Risk Analysis</button>
                        <button class="tab-btn whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm text-gray-500 hover:text-gray-700 hover:border-gray-300" data-tab="tab5">Decision Tree</button>
                        <button class="tab-btn whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm text-gray-500 hover:text-gray-700 hover:border-gray-300" data-tab="tab4">Sensitivity Analysis (Tornado)</button>
                        <button class="tab-btn whitespace-nowrap py-3 px-4 border-b-2 font-semibold text-sm text-gray-500 hover:text-gray-700 hover:border-gray-300" data-tab="tab3">Action Plan</button>
                    </nav>
                </div>

                <!-- Tabs Content -->
                <div class="p-6">
                    <!-- Tab 1: Matrix & Methodology -->
                    <div id="tab1" class="tab-content active">
                        <div class="space-y-8">
                            <div>
                                <h2 class="text-2xl font-semibold text-center mb-6">5x5 Risk Assessment Matrix</h2>
                                <div class="flex items-center justify-center">
                                    <div class="flex items-center">
                                        <div class="vertical-text text-center font-semibold text-gray-600 mr-2"><span class="inline-block transform -translate-y-2">LIKELIHOOD</span><svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 13l-5 5m0 0l-5-5m5 5V6" /></svg></div>
                                        <div id="risk-matrix-container" class="overflow-x-auto"></div>
                                    </div>
                                </div>
                                <div class="text-center font-semibold text-gray-600 mt-2"><svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 inline-block" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" /></svg><span class="inline-block transform translate-y-1">SEVERITY</span></div>
                                <div class="mt-6 flex flex-wrap justify-center gap-4 sm:gap-6">
                                    <div class="flex items-center"><div class="w-5 h-5 rounded-full bg-green-500 mr-2 border border-green-600"></div><span class="font-medium">Low (1-6)</span></div>
                                    <div class="flex items-center"><div class="w-5 h-5 rounded-full bg-yellow-400 mr-2 border border-yellow-500"></div><span class="font-medium">Medium (7-12)</span></div>
                                    <div class="flex items-center"><div class="w-5 h-5 rounded-full bg-red-500 mr-2 border border-red-600"></div><span class="font-medium">High (13-25)</span></div>
                                </div>
                            </div>
                            <div>
                                <h2 class="text-2xl font-semibold mb-4">Risk Matrix Methodology</h2>
                                <div class="overflow-x-auto">
                                    <table class="min-w-full border border-gray-200 divide-y divide-gray-200">
                                        <thead class="bg-gray-50">
                                            <tr>
                                                <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700">Concept</th>
                                                <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700">Level</th>
                                                <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700">Description</th>
                                            </tr>
                                        </thead>
                                        <tbody class="bg-white divide-y divide-gray-200">
                                            <tr><td rowspan="5" class="px-4 py-2 align-top font-semibold">Severity</td><td class="px-4 py-2">5 - Catastrophic</td><td class="px-4 py-2 text-sm">The consequences will be very harmful, and recovery may be difficult.</td></tr>
                                            <tr><td class="px-4 py-2">4 - Major</td><td class="px-4 py-2 text-sm">The consequences will be significant and may cause long-term damage.</td></tr>
                                            <tr><td class="px-4 py-2">3 - Moderate</td><td class="px-4 py-2 text-sm">The consequences of the risk will take time to mitigate.</td></tr>
                                            <tr><td class="px-4 py-2">2 - Minor</td><td class="px-4 py-2 text-sm">The consequences of the risk will be easily managed.</td></tr>
                                            <tr><td class="px-4 py-2">1 - Insignificant</td><td class="px-4 py-2 text-sm">The risk will have few consequences if it occurs.</td></tr>
                                            <tr class="bg-gray-50"><td colspan="3" class="h-4"></td></tr>
                                            <tr><td rowspan="5" class="px-4 py-2 align-top font-semibold">Likelihood</td><td class="px-4 py-2">5 - Very Likely</td><td class="px-4 py-2 text-sm">You can be fairly certain this risk will occur at some point.</td></tr>
                                            <tr><td class="px-4 py-2">4 - Likely</td><td class="px-4 py-2 text-sm">There is a high probability that this risk will occur.</td></tr>
                                            <tr><td class="px-4 py-2">3 - Possible</td><td class="px-4 py-2 text-sm">This risk may or may not occur (50/50 chance).</td></tr>
                                            <tr><td class="px-4 py-2">2 - Unlikely</td><td class="px-4 py-2 text-sm">There is a high probability that this risk will not occur.</td></tr>
                                            <tr><td class="px-4 py-2">1 - Very Unlikely</td><td class="px-4 py-2 text-sm">It is a remote possibility that this risk will occur.</td></tr>
                                            <tr class="bg-gray-50"><td colspan="3" class="h-4"></td></tr>
                                            <tr><td rowspan="3" class="px-4 py-2 align-top font-semibold">Impact</td><td class="px-4 py-2">High (13-25)</td><td class="px-4 py-2 text-sm">Top priority. Can derail your project if not addressed.</td></tr>
                                            <tr><td class="px-4 py-2">Medium (7-12)</td><td class="px-4 py-2 text-sm">Can cause setbacks but are manageable with proper planning.</td></tr>
                                            <tr><td class="px-4 py-2">Low (1-6)</td><td class="px-4 py-2 text-sm">Low-priority events. Unlikely to happen with insignificant consequences.</td></tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Tab 2: Risk Analysis -->
                    <div id="tab2" class="tab-content">
                        <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-6">
                            <h2 class="text-2xl font-semibold mb-2 sm:mb-0">Risk Identification & Analysis</h2>
                            <button id="add-risk-btn" class="bg-blue-600 text-white font-semibold py-2 px-4 rounded-lg hover:bg-blue-700 transition duration-300 flex items-center shadow-md"><svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" /></svg>Add Risk</button>
                        </div>
                        <div id="risk-list" class="space-y-4"></div>
                    </div>
                    <!-- Tab 6: Risk Strategies -->
                    <div id="tab6" class="tab-content">
                        <h2 class="text-2xl font-semibold mb-4">Risk Response Strategies</h2>
                        <p class="text-gray-600 mb-4">Use this guide to inform your Action Plan. The tool will suggest a strategy for each risk in the "Risk Analysis" tab.</p>
                        <div class="overflow-x-auto">
                            <table class="min-w-full border">
                                <thead class="bg-gray-50">
                                    <tr>
                                        <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Strategy</th>
                                        <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">When to Use</th>
                                        <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Description</th>
                                    </tr>
                                </thead>
                                <tbody class="bg-white text-sm">
                                    <tr>
                                        <td class="px-4 py-3 align-top font-semibold border-b">Avoid</td>
                                        <td class="px-4 py-3 align-top border-b">When a risk is very negative and outside acceptable thresholds.</td>
                                        <td class="px-4 py-3 align-top border-b">Actions to eliminate the threat, redirect the project, or, in extreme cases, cancel it if the risk is unacceptable.</td>
                                    </tr>
                                    <tr>
                                        <td class="px-4 py-3 align-top font-semibold border-b">Exploit</td>
                                        <td class="px-4 py-3 align-top border-b">When an opportunity (positive risk) is very high.</td>
                                        <td class="px-4 py-3 align-top border-b">Actions to ensure the opportunity materializes and to gain maximum benefit.</td>
                                    </tr>
                                    <tr>
                                        <td class="px-4 py-3 align-top font-semibold border-b">Transfer / Share</td>
                                        <td class="px-4 py-3 align-top border-b">When a risk is high and the organization cannot manage it effectively.</td>
                                        <td class="px-4 py-3 align-top border-b">Involve a third party. For threats, this means paying a premium (e.g., insurance). For opportunities, it means sharing the benefits.</td>
                                    </tr>
                                    <tr>
                                        <td class="px-4 py-3 align-top font-semibold border-b">Mitigate / Enhance</td>
                                        <td class="px-4 py-3 align-top border-b">To optimize the chances of achieving objectives.</td>
                                        <td class="px-4 py-3 align-top border-b"><strong>Mitigate</strong> is used to reduce the probability or impact of a threat. <strong>Enhance</strong> is used to increase the probability or impact of an opportunity.</td>
                                    </tr>
                                    <tr>
                                        <td class="px-4 py-3 align-top font-semibold">Accept</td>
                                        <td class="px-4 py-3 align-top">When a proactive response is not feasible or cost-effective.</td>
                                        <td class="px-4 py-3 align-top"><strong>Active:</strong> create a contingency reserve (time, money). <strong>Passive:</strong> no action taken, other than periodic review.</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                    <!-- Tab 5: Decision Tree -->
                    <div id="tab5" class="tab-content">
                        <h2 class="text-2xl font-semibold mb-4">Decision Tree Analysis Tool</h2>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                            <div class="space-y-6">
                                <div>
                                    <h3 class="text-xl font-semibold mb-3">How to Create a Decision Tree</h3>
                                    <div class="overflow-x-auto">
                                        <table class="min-w-full border">
                                            <thead class="bg-gray-50">
                                                <tr>
                                                    <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Step</th>
                                                    <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Action</th>
                                                </tr>
                                            </thead>
                                            <tbody class="bg-white">
                                                <tr><td class="px-4 py-2 align-top font-medium border-b">1. Start with an Idea</td><td class="px-4 py-2 text-sm border-b">Begin with a main decision. E.g., "Choose App Development Strategy."</td></tr>
                                                <tr><td class="px-4 py-2 align-top font-medium border-b">2. Add Choices</td><td class="px-4 py-2 text-sm border-b">Add branches for each possible choice, like "Develop New App," and enter its initial cost.</td></tr>
                                                <tr><td class="px-4 py-2 align-top font-medium border-b">3. Add Outcomes</td><td class="px-4 py-2 text-sm border-b">For each choice, add possible outcomes (e.g., "High Success," "Low Success"). Assign a probability (%) and a financial payoff to each.</td></tr>
                                                <tr><td class="px-4 py-2 align-top font-medium border-b">4. Calculate Values</td><td class="px-4 py-2 text-sm border-b">The tool calculates the Expected Value (EV) for each choice automatically.</td></tr>
                                                <tr><td class="px-4 py-2 align-top font-medium">5. Evaluate Results</td><td class="px-4 py-2 text-sm">Compare the EVs. The tool highlights the choice with the highest EV as the best financial decision.</td></tr>
                                            </tbody>
                                        </table>
                                    </div>
                                </div>
                                <div class="space-y-3">
                                    <h3 class="text-xl font-semibold">Probability Reference Guide</h3>
                                     <div class="overflow-x-auto">
                                        <table class="min-w-full border text-sm">
                                            <thead class="bg-gray-50">
                                                <tr>
                                                    <th class="px-4 py-2 text-left font-semibold text-gray-700 border-b">Term</th>
                                                    <th class="px-4 py-2 text-left font-semibold text-gray-700 border-b">Probability Range</th>
                                                </tr>
                                            </thead>
                                            <tbody class="bg-white">
                                                <tr><td class="px-4 py-2 border-b">Very High</td><td class="px-4 py-2 border-b">81% - 100%</td></tr>
                                                <tr><td class="px-4 py-2 border-b">High</td><td class="px-4 py-2 border-b">61% - 80%</td></tr>
                                                <tr><td class="px-4 py-2 border-b">Medium</td><td class="px-4 py-2 border-b">41% - 60%</td></tr>
                                                <tr><td class="px-4 py-2 border-b">Low</td><td class="px-4 py-2 border-b">21% - 40%</td></tr>
                                                <tr><td class="px-4 py-2">Very Low</td><td class="px-4 py-2">0% - 20%</td></tr>
                                            </tbody>
                                        </table>
                                    </div>
                                </div>
                            </div>
                            <div>
                                <h3 class="text-xl font-semibold mb-3">Interactive Decision Tree Builder</h3>
                                <div class="bg-gray-50 p-4 rounded-lg border space-y-4">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700">Main Decision</label>
                                        <input type="text" id="decision-title" placeholder="e.g., App Development Strategy" class="w-full p-2 border border-gray-300 rounded-md">
                                    </div>
                                    <div id="decision-choices-container" class="space-y-4"></div>
                                    <button id="add-decision-choice-btn" class="text-sm bg-blue-600 text-white font-semibold py-2 px-3 rounded-lg hover:bg-blue-700"><svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2 inline" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" /></svg>Add Choice</button>
                                    <div id="decision-summary" class="mt-4 p-3 bg-green-100 border border-green-300 rounded-md text-center font-semibold text-green-800"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- Tab 4: Sensitivity Analysis (Tornado Graph) -->
                    <div id="tab4" class="tab-content">
                        <h2 class="text-2xl font-semibold mb-4">Sensitivity Analysis (Tornado Graph)</h2>
                        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                            <div>
                                <h3 class="text-xl font-semibold mb-3">How to Create a Tornado Graph</h3>
                                <div class="overflow-x-auto">
                                    <table class="min-w-full border">
                                        <thead class="bg-gray-50">
                                            <tr>
                                                <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Step</th>
                                                <th class="px-4 py-2 text-left text-sm font-semibold text-gray-700 border-b">Action</th>
                                            </tr>
                                        </thead>
                                        <tbody class="bg-white">
                                            <tr><td class="px-4 py-2 align-top font-medium border-b">1. List Variables</td><td class="px-4 py-2 text-sm border-b">Use the tool on the right to list key variables or risks.</td></tr>
                                            <tr><td class="px-4 py-2 align-top font-medium border-b">2. Set Baseline</td><td class="px-4 py-2 text-sm border-b">Determine the project's expected value (e.g., budget) below.</td></tr>
                                            <tr><td class="px-4 py-2 align-top font-medium border-b">3. Define Ranges</td><td class="px-4 py-2 text-sm border-b">For each variable, enter the best-case (low impact) and worst-case (high impact) values.</td></tr>
                                            <tr><td class="px-4 py-2 align-top font-medium border-b">4. Calculate Swing</td><td class="px-4 py-2 text-sm border-b">The tool automatically calculates the difference ('swing') between the values.</td></tr>
                                            <tr><td class="px-4 py-2 align-top font-medium">5. Visualize</td><td class="px-4 py-2 text-sm">The graph sorts variables by their swing, showing the most sensitive items at the top.</td></tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                            <div>
                                <h3 class="text-xl font-semibold mb-3">Graph Data & Visualization</h3>
                                <div class="bg-gray-50 p-4 rounded-lg border">
                                    <div class="grid grid-cols-12 gap-2 items-center mb-2">
                                        <div class="col-span-5"><label class="block text-xs font-bold text-gray-500 uppercase">Variable Name</label></div>
                                        <div class="col-span-3"><label class="block text-xs font-bold text-gray-500 uppercase">Low Impact</label></div>
                                        <div class="col-span-3"><label class="block text-xs font-bold text-gray-500 uppercase">High Impact</label></div>
                                        <div class="col-span-1"></div>
                                    </div>
                                    <div id="tornado-data-entry"></div>
                                    <button id="add-tornado-variable-btn" class="mt-2 text-sm bg-green-600 text-white font-semibold py-2 px-3 rounded-lg hover:bg-green-700 transition"><svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2 inline" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" clip-rule="evenodd" /></svg>Add Variable</button>
                                </div>
                                <div class="mt-4">
                                    <label for="baseline-value" class="block text-sm font-medium text-gray-700">Project Baseline Value</label>
                                    <input type="number" id="baseline-value" value="100000" class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm">
                                </div>
                                <div id="tornado-graph-container" class="mt-4 space-y-3 p-4 bg-gray-50 rounded-lg border min-h-[200px]"></div>
                            </div>
                        </div>
                    </div>
                    <!-- Tab 3: Action Plan -->
                    <div id="tab3" class="tab-content">
                        <h2 class="text-2xl font-semibold mb-4">Summary Table: Action Plan</h2>
                        <div class="overflow-x-auto">
                            <table class="min-w-full divide-y divide-gray-200"><thead class="bg-gray-100"><tr><th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Risk</th><th scope="col" class="px-6 py-3 text-center text-xs font-bold text-gray-600 uppercase tracking-wider">Impact Score</th><th scope="col" class="px-6 py-3 text-center text-xs font-bold text-gray-600 uppercase tracking-wider">Risk Level</th><th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-600 uppercase tracking-wider">Mitigation Plan</th></tr></thead><tbody id="summary-table-body" class="bg-white divide-y divide-gray-200"></tbody></table>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <!-- Hidden Templates -->
    <div id="risk-template" class="hidden">
        <div class="risk-card border-2 border-gray-200 p-4 rounded-lg bg-gray-50">
            <div class="grid grid-cols-12 gap-x-4 gap-y-2 items-end">
                <div class="col-span-12"><label class="block text-sm font-medium text-gray-700">Risk Description</label><input type="text" placeholder="e.g., Customer data breach" class="risk-description w-full p-2 border border-gray-300 rounded-md"></div>
                
                <div class="col-span-6 sm:col-span-3"><label class="block text-sm font-medium text-gray-700">Severity</label><select class="severity-select w-full p-2 border border-gray-300 rounded-md"><option value="0" selected disabled>Select</option><option value="1">1 - Insignificant</option><option value="2">2 - Minor</option><option value="3">3 - Moderate</option><option value="4">4 - Major</option><option value="5">5 - Catastrophic</option></select></div>
                <div class="col-span-6 sm:col-span-3"><label class="block text-sm font-medium text-gray-700">Likelihood</label><select class="likelihood-select w-full p-2 border border-gray-300 rounded-md"><option value="0" selected disabled>Select</option><option value="1">1 - Very Unlikely</option><option value="2">2 - Unlikely</option><option value="3">3 - Possible</option><option value="4">4 - Likely</option><option value="5">5 - Very Likely</option></select></div>
                <div class="col-span-6 sm:col-span-3"><label class="block text-sm font-medium text-gray-700">Risk Type</label><select class="risk-type-select w-full p-2 border border-gray-300 rounded-md"><option value="N/A" selected>Select</option><option value="Threat">Threat</option><option value="Opportunity">Opportunity</option></select></div>
                <div class="col-span-6 sm:col-span-3 flex gap-2">
                    <div class="flex-1"><label class="block text-sm font-medium text-gray-700">Impact</label><p class="impact-score text-xl font-bold p-1.5 bg-white border border-gray-300 rounded-md text-center">--</p></div>
                    <div class="flex-1"><label class="block text-sm font-medium text-gray-700">Level</label><p class="risk-level font-bold p-2 rounded-md text-center text-white bg-gray-400">N/A</p></div>
                </div>

                <div class="col-span-12"><label class="block text-sm font-medium text-gray-700">Suggested Strategy</label><div class="suggested-strategy p-2 bg-blue-50 border border-blue-200 text-blue-800 rounded-md text-sm font-semibold h-[42px] flex items-center">Select Risk Type...</div></div>

                <div class="col-span-11"><label class="block text-sm font-medium text-gray-700">Action / Mitigation Plan</label><textarea placeholder="Describe the steps to prevent or mitigate this risk..." class="mitigation-plan w-full p-2 border border-gray-300 rounded-md" rows="1"></textarea></div>
                <div class="col-span-1"><button class="delete-risk-btn w-full bg-red-500 text-white p-2 rounded-md hover:bg-red-600"><svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 mx-auto" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" /></svg></button></div>
            </div>
        </div>
    </div>
    <div id="tornado-row-template" class="hidden"><div class="tornado-row grid grid-cols-12 gap-2 items-center mb-2"><div class="col-span-5"><input type="text" placeholder="Variable Name" class="tornado-name w-full p-2 text-sm border border-gray-300 rounded-md"></div><div class="col-span-3"><input type="number" placeholder="Low" class="tornado-low w-full p-2 text-sm border border-gray-300 rounded-md"></div><div class="col-span-3"><input type="number" placeholder="High" class="tornado-high w-full p-2 text-sm border border-gray-300 rounded-md"></div><div class="col-span-1"><button class="delete-tornado-row-btn w-full bg-gray-200 text-gray-600 p-2 rounded-md hover:bg-red-200 hover:text-red-800 transition">X</button></div></div></div>
    <div id="decision-choice-template" class="hidden"><div class="decision-choice-card border-2 p-3 rounded-lg space-y-3"><div class="flex justify-between items-start"><div class="flex-grow space-y-2"><div class="flex items-center gap-2"><input type="text" placeholder="Choice Name" class="decision-choice-name text-lg font-semibold border-b-2 w-full"><input type="number" placeholder="Cost" class="decision-choice-cost w-28 p-1 border rounded-md text-sm"></div><div class="outcomes-container space-y-2 pl-4 border-l-2"><div class="grid grid-cols-12 gap-2 items-center text-xs font-bold text-gray-500 uppercase"><div class="col-span-5">Outcome</div><div class="col-span-3">Prob. %</div><div class="col-span-3">Payoff/Cost</div></div></div><button class="add-outcome-btn text-xs bg-gray-200 text-gray-700 py-1 px-2 rounded-md hover:bg-gray-300">+ Add Outcome</button></div><button class="delete-choice-btn text-gray-400 hover:text-red-500 ml-2">✖</button></div><div class="p-2 bg-gray-100 rounded-md text-center"><span class="font-semibold">Expected Value (EV): </span><span class="ev-value font-bold">...</span><p class="probability-warning text-red-500 text-xs mt-1 hidden">Probabilities must add up to 100%</p></div></div></div>
    <div id="decision-outcome-template" class="hidden"><div class="outcome-row grid grid-cols-12 gap-2 items-center"><div class="col-span-5"><input type="text" placeholder="Outcome Name" class="outcome-name w-full p-1 border rounded-md text-sm"></div><div class="col-span-3"><input type="number" placeholder="e.g. 55" class="outcome-prob w-full p-1 border rounded-md text-sm"></div><div class="col-span-3"><input type="number" placeholder="Payoff(+) / Cost(-)" class="outcome-payoff w-full p-1 border rounded-md text-sm"></div><div class="col-span-1"><button class="delete-outcome-btn text-gray-400 hover:text-red-500">✖</button></div></div></div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // --- CONSTANTS AND DEFINITIONS ---
            const severityLevels = ["Insignificant (1)", "Minor (2)", "Moderate (3)", "Major (4)", "Catastrophic (5)"];
            const likelihoodLevels = ["Very Likely (5)", "Likely (4)", "Possible (3)", "Unlikely (2)", "Very Unlikely (1)"];

            // --- ELEMENT SELECTORS ---
            const tabs = document.querySelectorAll('.tab-btn');
            const tabContents = document.querySelectorAll('.tab-content');
            const matrixContainer = document.getElementById('risk-matrix-container');
            const addRiskBtn = document.getElementById('add-risk-btn');
            const riskList = document.getElementById('risk-list');
            const riskTemplate = document.getElementById('risk-template');
            const summaryTableBody = document.getElementById('summary-table-body');
            const tornadoContainer = document.getElementById('tornado-graph-container');
            const baselineInput = document.getElementById('baseline-value');
            const addTornadoBtn = document.getElementById('add-tornado-variable-btn');
            const tornadoDataEntry = document.getElementById('tornado-data-entry');
            const tornadoRowTemplate = document.getElementById('tornado-row-template');
            const decisionChoicesContainer = document.getElementById('decision-choices-container');
            const addDecisionChoiceBtn = document.getElementById('add-decision-choice-btn');
            const decisionChoiceTemplate = document.getElementById('decision-choice-template');
            const decisionOutcomeTemplate = document.getElementById('decision-outcome-template');
            const decisionSummary = document.getElementById('decision-summary');
            const decisionTitleInput = document.getElementById('decision-title');

            // --- INITIAL DATA ---
            const initialRisks = [
                { description: "Customer data breach", severity: 4, likelihood: 4, type: "Threat", plan: "Implement end-to-end encryption and quarterly security audits." },
                { description: "New market opportunity", severity: 3, likelihood: 3, type: "Opportunity", plan: "Develop a targeted marketing campaign." },
            ];
            
            const initialTornadoData = [
                 { name: "Supplier Cost Increase", low: 110000, high: 150000 },
                 { name: "Scope Creep", low: 105000, high: 135000 },
                 { name: "Technical Issues", low: 95000, high: 120000 },
            ];
            
            const initialDecisionData = {
                title: "App Development Strategy",
                choices: [
                    { name: "Develop New Task App", cost: 50000, outcomes: [{ name: "High Success", prob: 55, payoff: 200000 }, { name: "Low Success", prob: 45, payoff: 150000 }] },
                    { name: "Update Existing App", cost: 25000, outcomes: [{ name: "High Success", prob: 60, payoff: 100000 }, { name: "Low Success", prob: 40, payoff: 80000 }] },
                    { name: "Develop Team App", cost: 75000, outcomes: [{ name: "High Success", prob: 55, payoff: 250000 }, { name: "Low Success", prob: 45, payoff: 200000 }] }
                ]
            };

            // --- Tab Logic ---
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    tabs.forEach(item => item.classList.remove('active'));
                    tab.classList.add('active');
                    const target = tab.getAttribute('data-tab');
                    tabContents.forEach(content => content.classList.remove('active'));
                    document.getElementById(target).classList.add('active');
                });
            });

            // --- Utility Functions ---
            const getRiskLevel = (score) => {
                if (score >= 13) return { text: 'High', color: 'bg-red-500', borderColor: 'border-red-500' };
                if (score >= 7) return { text: 'Medium', color: 'bg-yellow-400', borderColor: 'border-yellow-400' };
                if (score >= 1) return { text: 'Low', color: 'bg-green-500', borderColor: 'border-green-500' };
                return { text: 'N/A', color: 'bg-gray-400', borderColor: 'border-gray-200' };
            };
            const formatCurrency = (value) => new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(value);

            // --- Main Update Functions ---
            function updateSummaryTable() {
                summaryTableBody.innerHTML = '';
                const riskCards = document.querySelectorAll('.risk-card');
                if (riskCards.length === 0) {
                    summaryTableBody.innerHTML = `<tr><td colspan="4" class="text-center text-gray-500 py-4">No risks defined. Add one to get started.</td></tr>`;
                    return;
                }
                riskCards.forEach(card => {
                    const description = card.querySelector('.risk-description').value || 'N/A';
                    const impact = card.querySelector('.impact-score').textContent;
                    const plan = card.querySelector('.mitigation-plan').value || 'No plan defined';
                    const score = parseInt(impact) || 0;
                    const level = getRiskLevel(score);
                    const row = document.createElement('tr');
                    row.innerHTML = `<td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${description}</td><td class="px-6 py-4 whitespace-nowrap text-sm text-gray-700 text-center font-bold">${impact}</td><td class="px-6 py-4 whitespace-nowrap text-sm"><div class="table-cell-level ${level.color}">${level.text}</div></td><td class="px-6 py-4 whitespace-normal text-sm text-gray-700">${plan}</td>`;
                    summaryTableBody.appendChild(row);
                });
            }

            function updateTornadoGraph() {
                tornadoContainer.innerHTML = '';
                const baseline = parseFloat(baselineInput.value) || 0;
                const tornadoRows = document.querySelectorAll('.tornado-row');
                let risksData = [];
                tornadoRows.forEach(row => {
                    const low = parseFloat(row.querySelector('.tornado-low').value);
                    const high = parseFloat(row.querySelector('.tornado-high').value);
                    if (!isNaN(low) && !isNaN(high) && high > low) {
                        risksData.push({ name: row.querySelector('.tornado-name').value || 'Unnamed Variable', low, high, swing: high - low });
                    }
                });
                if (risksData.length === 0) {
                    tornadoContainer.innerHTML = `<p class="text-center text-gray-500">Add variables and their impact values to generate the graph.</p>`;
                    return;
                }
                risksData.sort((a, b) => b.swing - a.swing);
                const maxSwing = Math.max(...risksData.map(r => Math.max(Math.abs(r.low - baseline), Math.abs(r.high - baseline))));
                if (maxSwing === 0) return;
                risksData.forEach(risk => {
                    const lowDiff = baseline - risk.low;
                    const highDiff = risk.high - baseline;
                    const lowWidth = (lowDiff / maxSwing) * 50;
                    const highWidth = (highDiff / maxSwing) * 50;
                    const barHTML = `<div class="text-sm font-medium text-gray-800 truncate" title="${risk.name}">${risk.name}</div><div class="flex items-center w-full"><div class="w-1/2 flex justify-end"><div class="tornado-bar bg-blue-400 h-6 rounded-l-md" style="width: ${lowWidth > 0 ? lowWidth : 0}%" title="Low: ${risk.low}"></div></div><div class="w-px bg-gray-400 h-8 -ml-px"></div><div class="w-1/2 flex justify-start"><div class="tornado-bar bg-red-400 h-6 rounded-r-md" style="width: ${highWidth > 0 ? highWidth : 0}%" title="High: ${risk.high}"></div></div></div>`;
                    tornadoContainer.innerHTML += barHTML;
                });
                tornadoContainer.innerHTML += `<div class="text-center text-xs text-gray-500 mt-2">Baseline: ${baseline.toLocaleString()}</div>`;
            }
            
            function calculateDecisionTree() {
                let bestChoice = { name: null, ev: -Infinity };
                const choiceCards = document.querySelectorAll('.decision-choice-card');
                choiceCards.forEach(card => {
                    let totalExpectedValue = 0;
                    let totalProbability = 0;
                    const cost = parseFloat(card.querySelector('.decision-choice-cost').value) || 0;
                    const outcomes = card.querySelectorAll('.outcome-row');
                    outcomes.forEach(outcome => {
                        const prob = parseFloat(outcome.querySelector('.outcome-prob').value) || 0;
                        const payoff = parseFloat(outcome.querySelector('.outcome-payoff').value) || 0;
                        totalExpectedValue += (payoff * (prob / 100));
                        totalProbability += prob;
                    });
                    
                    const finalEV = totalExpectedValue - cost;
                    card.querySelector('.ev-value').textContent = formatCurrency(finalEV);
                    
                    const warning = card.querySelector('.probability-warning');
                    if (Math.round(totalProbability) !== 100 && outcomes.length > 0) {
                        warning.classList.remove('hidden');
                    } else {
                        warning.classList.add('hidden');
                    }

                    if (finalEV > bestChoice.ev) {
                        bestChoice = { name: card.querySelector('.decision-choice-name').value || "Unnamed Choice", ev: finalEV };
                    }
                });

                if (bestChoice.name) {
                    decisionSummary.innerHTML = `Best Choice: <strong class="font-bold">${bestChoice.name}</strong> with an Expected Value of <strong class="font-bold">${formatCurrency(bestChoice.ev)}</strong>.`;
                } else {
                    decisionSummary.innerHTML = 'Add choices and outcomes to see the best decision.';
                }
            }

            // --- Risk Card Functions ---
            function addEventListenersToCard(card) {
                const inputs = card.querySelectorAll('select, input, textarea');
                inputs.forEach(input => input.addEventListener('input', updateRiskCalculationAndSummary));
                card.querySelector('.delete-risk-btn').addEventListener('click', () => {
                    card.classList.add('opacity-0', 'scale-95');
                    setTimeout(() => { card.remove(); updateSummaryTable(); }, 300);
                });
            }
            
            function updateRiskCalculationAndSummary(event) {
                const card = event.target.closest('.risk-card');
                const severity = parseInt(card.querySelector('.severity-select').value) || 0;
                const likelihood = parseInt(card.querySelector('.likelihood-select').value) || 0;
                const riskType = card.querySelector('.risk-type-select').value;
                const impactScoreEl = card.querySelector('.impact-score');
                const riskLevelEl = card.querySelector('.risk-level');
                const suggestionEl = card.querySelector('.suggested-strategy');
                
                let suggestion = "Select Risk Type...";

                if (severity > 0 && likelihood > 0) {
                    const score = severity * likelihood;
                    const level = getRiskLevel(score);
                    impactScoreEl.textContent = score;
                    riskLevelEl.textContent = level.text;
                    riskLevelEl.className = 'risk-level font-bold p-2 rounded-md text-center text-white ' + level.color;
                    card.className = `risk-card border-2 p-4 rounded-lg bg-gray-50 ${level.borderColor}`;

                    if (riskType !== 'N/A') {
                        if (level.text === 'High') {
                            suggestion = (riskType === 'Threat') ? 'Consider **Avoid** or **Transfer**' : '**Exploit**';
                        } else if (level.text === 'Medium') {
                            suggestion = (riskType === 'Threat') ? '**Mitigate**' : '**Enhance**';
                        } else if (level.text === 'Low') {
                            suggestion = '**Accept**';
                        }
                    }
                } else {
                    impactScoreEl.textContent = '--';
                    riskLevelEl.textContent = 'N/A';
                    riskLevelEl.className = 'risk-level font-bold p-2 rounded-md text-center text-white bg-gray-400';
                    card.className = 'risk-card border-2 border-gray-200 p-4 rounded-lg bg-gray-50';
                }
                suggestionEl.innerHTML = `Suggested: ${suggestion}`;
                updateSummaryTable();
            }

            function createNewRiskCard(riskData = {}) {
                const newCard = riskTemplate.firstElementChild.cloneNode(true);
                if (riskData.description) newCard.querySelector('.risk-description').value = riskData.description;
                if (riskData.severity) newCard.querySelector('.severity-select').value = riskData.severity;
                if (riskData.likelihood) newCard.querySelector('.likelihood-select').value = riskData.likelihood;
                if (riskData.type) newCard.querySelector('.risk-type-select').value = riskData.type;
                if (riskData.plan) newCard.querySelector('.mitigation-plan').value = riskData.plan;
                riskList.appendChild(newCard);
                addEventListenersToCard(newCard);
                newCard.querySelector('.severity-select').dispatchEvent(new Event('change'));
            }
            
            // --- Tornado Graph Functions ---
            function createNewTornadoRow(data = {}) {
                const newRow = tornadoRowTemplate.firstElementChild.cloneNode(true);
                if (data.name) newRow.querySelector('.tornado-name').value = data.name;
                if (data.low) newRow.querySelector('.tornado-low').value = data.low;
                if (data.high) newRow.querySelector('.tornado-high').value = data.high;
                newRow.querySelectorAll('input').forEach(input => input.addEventListener('input', updateTornadoGraph));
                newRow.querySelector('.delete-tornado-row-btn').addEventListener('click', () => { newRow.remove(); updateTornadoGraph(); });
                tornadoDataEntry.appendChild(newRow);
            }

            // --- Decision Tree Functions ---
            function createNewDecisionChoice(choiceData = {}) {
                const newChoice = decisionChoiceTemplate.firstElementChild.cloneNode(true);
                if (choiceData.name) newChoice.querySelector('.decision-choice-name').value = choiceData.name;
                if (choiceData.cost) newChoice.querySelector('.decision-choice-cost').value = choiceData.cost;
                
                newChoice.querySelectorAll('input').forEach(input => input.addEventListener('input', calculateDecisionTree));
                newChoice.querySelector('.add-outcome-btn').addEventListener('click', () => createNewOutcome(newChoice));
                newChoice.querySelector('.delete-choice-btn').addEventListener('click', () => { newChoice.remove(); calculateDecisionTree(); });
                decisionChoicesContainer.appendChild(newChoice);

                if (choiceData.outcomes && choiceData.outcomes.length > 0) {
                    choiceData.outcomes.forEach(outcomeData => createNewOutcome(newChoice, outcomeData));
                } else {
                    createNewOutcome(newChoice); 
                }
            }

            function createNewOutcome(choiceCard, outcomeData = {}) {
                const outcomesContainer = choiceCard.querySelector('.outcomes-container');
                const newOutcome = decisionOutcomeTemplate.firstElementChild.cloneNode(true);
                if(outcomeData.name) newOutcome.querySelector('.outcome-name').value = outcomeData.name;
                if(outcomeData.prob) newOutcome.querySelector('.outcome-prob').value = outcomeData.prob;
                if(outcomeData.payoff) newOutcome.querySelector('.outcome-payoff').value = outcomeData.payoff;

                newOutcome.querySelectorAll('input').forEach(input => input.addEventListener('input', calculateDecisionTree));
                newOutcome.querySelector('.delete-outcome-btn').addEventListener('click', () => { newOutcome.remove(); calculateDecisionTree(); });
                outcomesContainer.appendChild(newOutcome);
            }

            // --- Visual Matrix Generation ---
            function generateMatrix() {
                let tableHTML = '<table class="border-collapse text-center">';
                tableHTML += '<thead><tr><th class="border border-gray-300 p-2 w-40"></th>';
                severityLevels.forEach(level => { tableHTML += `<th class="border border-gray-300 p-2 font-semibold text-xs sm:text-sm">${level}</th>`; });
                tableHTML += '</tr></thead><tbody>';
                likelihoodLevels.forEach((level, rowIndex) => {
                    const likelihoodValue = 5 - rowIndex;
                    tableHTML += `<tr><td class="border border-gray-300 p-2 font-semibold text-xs sm:text-sm">${level}</td>`;
                    severityLevels.forEach((_, colIndex) => {
                        const severityValue = colIndex + 1;
                        const score = likelihoodValue * severityValue;
                        const levelInfo = getRiskLevel(score);
                        tableHTML += `<td class="border border-gray-300 p-2 sm:p-4 font-bold text-base sm:text-lg ${levelInfo.color} text-white">${score}</td>`;
                    });
                    tableHTML += '</tr>';
                });
                tableHTML += '</tbody></table>';
                matrixContainer.innerHTML = tableHTML;
            }

            // --- Initialization ---
            initialRisks.forEach(risk => createNewRiskCard(risk));
            initialTornadoData.forEach(data => createNewTornadoRow(data));
            
            addRiskBtn.addEventListener('click', () => createNewRiskCard());
            addTornadoBtn.addEventListener('click', () => createNewTornadoRow());
            baselineInput.addEventListener('input', updateTornadoGraph);
            addDecisionChoiceBtn.addEventListener('click', () => createNewDecisionChoice());
            
            decisionTitleInput.value = initialDecisionData.title;
            initialDecisionData.choices.forEach(choice => createNewDecisionChoice(choice));

            generateMatrix();
            updateSummaryTable();
            updateTornadoGraph();
            calculateDecisionTree();
        });
    </script>
</body>
</html>
