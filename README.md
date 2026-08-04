<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ប្រព័ន្ធទិន្នន័យស្ថិតិ និងសេដ្ឋកិច្ច ខេត្តកោះកុង</title>
    <!-- Tailwind CSS CDN (សម្រាប់ម៉ូត និងរចនាបថ) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js CDN (សម្រាប់បង្កើតដ្យាក្រាម) -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Google Fonts for Khmer -->
    <link href="https://fonts.googleapis.com/css2?family=Kantumruy+Pro:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Kantumruy Pro', sans-serif;
            background-color: #f8fafc;
        }
    </style>
</head>
<body class="text-slate-800">

    <!-- Header Section -->
    <header class="bg-indigo-900 text-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 py-6 sm:px-6 lg:px-8 flex flex-col md:flex-row justify-between items-center">
            <div>
                <h1 class="text-2xl font-bold">ប្រព័ន្ធទិន្នន័យស្ថិតិ និងសេដ្ឋកិច្ច ខេត្តកោះកុង</h1>
                <p class="text-indigo-200 text-sm mt-1">Koh Kong Provincial Demographic & Economic Data Portal</p>
            </div>
            <div class="mt-4 md:mt-0">
                <span class="inline-block bg-indigo-800 text-indigo-100 px-3 py-1 rounded-full text-xs font-semibold">
                    បច្ចុប្បន្នភាពចុងក្រោយ៖ ២០២៦
                </span>
            </div>
        </div>
    </header>

    <!-- Main Container -->
    <main class="max-w-7xl mx-auto px-4 py-8 sm:px-6 lg:px-8 space-y-8">

        <!-- Summary Cards -->
        <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <p class="text-xs font-semibold text-slate-500 uppercase">ប្រជាជនសរុប (ព្យាករណ៍)</p>
                <h3 class="text-2xl font-bold text-indigo-900 mt-2">១៤៥,៨០០ នាក់</h3>
                <span class="text-xs text-emerald-600 font-semibold">↑ ១.៨% ក្នុងមួយឆ្នាំ</span>
            </div>
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <p class="text-xs font-semibold text-slate-500 uppercase">អត្រាភាពក្រីក្រមធ្យម</p>
                <h3 class="text-2xl font-bold text-indigo-900 mt-2">១២.៤%</h3>
                <span class="text-xs text-emerald-600 font-semibold">↓ ថយចុះជាលំដាប់</span>
            </div>
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <p class="text-xs font-semibold text-slate-500 uppercase">កំណើនសេដ្ឋកិច្ចខេត្ត (GRDP)</p>
                <h3 class="text-2xl font-bold text-indigo-900 mt-2">៦.៥%</h3>
                <span class="text-xs text-indigo-600 font-semibold">វិស័យទេសចរណ៍ និងឧស្សាហកម្ម</span>
            </div>
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <p class="text-xs font-semibold text-slate-500 uppercase">ចំនួន ក្រុង/ស្រុក</p>
                <h3 class="text-2xl font-bold text-indigo-900 mt-2">៧ ក្រុង/ស្រុក</h3>
                <span class="text-xs text-slate-500 font-semibold">២៩ ឃុំ/សង្កាត់</span>
            </div>
        </div>

        <!-- Charts Section -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
            <!-- Chart 1: Population Structure -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <h2 class="text-lg font-bold text-slate-800 mb-4 border-l-4 border-indigo-600 pl-3">
                    រចនាសម្ព័ន្ធអាយុប្រជាជន (Demographic Age Groups)
                </h2>
                <div class="relative h-64">
                    <canvas id="ageGroupChart"></canvas>
                </div>
            </div>

            <!-- Chart 2: Economic Growth Projections -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <h2 class="text-lg font-bold text-slate-800 mb-4 border-l-4 border-indigo-600 pl-3">
                    ការព្យាករណ៍កំណើនប្រជាជន និងសេដ្ឋកិច្ច
                </h2>
                <div class="relative h-64">
                    <canvas id="growthChart"></canvas>
                </div>
            </div>
        </div>

        <!-- Data Table Section -->
        <div class="bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
            <div class="p-6 border-b border-slate-200 flex flex-col md:flex-row justify-between items-md-center gap-4">
                <div>
                    <h2 class="text-lg font-bold text-slate-800 border-l-4 border-indigo-600 pl-3">
                        ទិន្នន័យស្ថិតិតាម ក្រុង/ស្រុក (Provincial District Data)
                    </h2>
                    <p class="text-xs text-slate-500 mt-1 pl-4">រួមបញ្ចូលទិន្នន័យប្រជាសាស្ត្រ អត្រាភាពក្រីក្រ និងភាពងាយរងគ្រោះ</p>
                </div>
                <!-- Search Box -->
                <div>
                    <input type="text" id="searchInput" onkeyup="filterTable()" placeholder="ស្វែងរក ក្រុង/ស្រុក..." 
                           class="px-4 py-2 text-sm border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 w-full md:w-64">
                </div>
            </div>

            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse" id="dataTable">
                    <thead>
                        <tr class="bg-slate-50 text-slate-600 text-xs font-semibold uppercase tracking-wider border-b border-slate-200">
                            <th class="py-3 px-6">ក្រុង/ស្រុក</th>
                            <th class="py-3 px-6">ចំនួនឃុំ/សង្កាត់</th>
                            <th class="py-3 px-6 text-right">ប្រជាជនសរុប</th>
                            <th class="py-3 px-6 text-right">អត្រាភាពក្រីក្រ (%)</th>
                            <th class="py-3 px-6 text-right">គ្រួសារងាយរងគ្រោះ</th>
                            <th class="py-3 px-6 text-center">ស្ថានភាពសេដ្ឋកិច្ច</th>
                        </tr>
                    </thead>
                    <tbody class="divide-y divide-slate-200 text-sm">
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ក្រុងខេមរភូមិន្ទ</td>
                            <td class="py-4 px-6">៣ សង្កាត់</td>
                            <td class="py-4 px-6 text-right font-mono">៤១,៥០០</td>
                            <td class="py-4 px-6 text-right">៨.២%</td>
                            <td class="py-4 px-6 text-right font-mono">៦៥០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-emerald-100 text-emerald-800 font-medium">ពាណិជ្ជកម្ម/សេវាកម្ម</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកបូទុមសាគរ</td>
                            <td class="py-4 px-6">៤ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">២២,៨០០</td>
                            <td class="py-4 px-6 text-right">១៤.៥%</td>
                            <td class="py-4 px-6 text-right font-mono">៨២០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-blue-100 text-blue-800 font-medium">កសិ-ឧស្សាហកម្ម</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកស្រែអំបិល</td>
                            <td class="py-4 px-6">៦ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">៣៨,២០០</td>
                            <td class="py-4 px-6 text-right">១១.៨%</td>
                            <td class="py-4 px-6 text-right font-mono">១,០៥០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-indigo-100 text-indigo-800 font-medium">ដឹកជញ្ជូន/កសិកម្ម</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកកោះកុង</td>
                            <td class="py-4 px-6">៤ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">១១,៤០០</td>
                            <td class="py-4 px-6 text-right">១៦.២%</td>
                            <td class="py-4 px-6 text-right font-mono">៤៨០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-amber-100 text-amber-800 font-medium">នេសាទ/ទេសចរណ៍</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកមណ្ឌលសីមា</td>
                            <td class="py-4 px-6">៣ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">១៨,៩០០</td>
                            <td class="py-4 px-6 text-right">៩.៥%</td>
                            <td class="py-4 px-6 text-right font-mono">៤១០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-emerald-100 text-emerald-800 font-medium">ពាណិជ្ជកម្មព្រំដែន</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកថ្មបាំង</td>
                            <td class="py-4 px-6">៦ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">៩,៦០០</td>
                            <td class="py-4 px-6 text-right">១៨.០%</td>
                            <td class="py-4 px-6 text-right font-mono">៥២០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-teal-100 text-teal-800 font-medium">អេកូទេសចរណ៍/កសិកម្ម</span>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-50">
                            <td class="py-4 px-6 font-semibold text-indigo-900">ស្រុកគិរីសាគរ</td>
                            <td class="py-4 px-6">៣ ឃុំ</td>
                            <td class="py-4 px-6 text-right font-mono">៣,៤០០</td>
                            <td class="py-4 px-6 text-right">១៣.០%</td>
                            <td class="py-4 px-6 text-right font-mono">១១៩០</td>
                            <td class="py-4 px-6 text-center">
                                <span class="px-2.5 py-1 text-xs rounded-full bg-purple-100 text-purple-800 font-medium">អភិវឌ្ឍន៍ទេសចរណ៍</span>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="bg-slate-900 text-slate-400 text-sm mt-12 py-6 border-t border-slate-800">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <p>© ២០២៦ ប្រព័ន្ធព័ត៌មានទិន្នន័យខេត្តកោះកុង | រក្សាសិទ្ធិគ្រប់យ៉ាង</p>
            <p class="text-xs text-slate-500 mt-1">Host ឥតគិតថ្លៃដោយរលូននៅលើ GitHub Pages</p>
        </div>
    </footer>

    <!-- JavaScript for Charts & Search -->
    <script>
        // 1. Chart: Age Groups (Pie Chart)
        const ctxAge = document.getElementById('ageGroupChart').getContext('2d');
        new Chart(ctxAge, {
            type: 'doughnut',
            data: {
                labels: ['០ - ១៤ ឆ្នាំ (កុមារ)', '១៥ - ៦៤ ឆ្នាំ (វ័យလုပ်ငန်း)', '៦៥ ឆ្នាំឡើង (មនុស្សចាស់)'],
                datasets: [{
                    data: [28, 65, 7],
                    backgroundColor: ['#3b82f6', '#10b981', '#f59e0b'],
                    borderWidth: 0
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' }
                }
            }
        });

        // 2. Chart: Growth Projections (Line Chart)
        const ctxGrowth = document.getElementById('growthChart').getContext('2d');
        new Chart(ctxGrowth, {
            type: 'line',
            data: {
                labels: ['២០២០', '២០២២', '២០២៤', '២០២៦', '២០២៨ (ព្យាករណ៍)', '២០៣០ (ព្យាករណ៍)'],
                datasets: [{
                    label: 'ប្រជាជនសរុប (ពាន់នាក់)',
                    data: [132, 138, 142, 145.8, 150.5, 156],
                    borderColor: '#4f46e5',
                    backgroundColor: 'rgba(79, 70, 229, 0.1)',
                    fill: true,
                    tension: 0.3
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'bottom' }
                }
            }
        });

        // 3. Table Search Function
        function filterTable() {
            const input = document.getElementById('searchInput');
            const filter = input.value.toLowerCase();
            const table = document.getElementById('dataTable');
            const trs = table.getElementsByTagName('tr');

            for (let i = 1; i < trs.length; i++) {
                const td = trs[i].getElementsByTagName('td')[0];
                if (td) {
                    const textValue = td.textContent || td.innerText;
                    if (textValue.toLowerCase().indexOf(filter) > -1) {
                        trs[i].style.display = "";
                    } else {
                        trs[i].style.display = "none";
                    }
                }
            }
        }
    </script>
</body>
</html>
