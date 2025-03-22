
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>QA Test Environments</title>
  <style>
    /* Import modern fonts */
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap');

    :root {
        --primary-color: #3b82f6; /* Vibrant blue */
        --secondary-color: #9333ea; /* Vibrant purple */
        --background-color: #f9fafb; /* Light background */
        --card-bg: #ffffff; /* Card background */
        --text-color: #1f2937; /* Dark text */
        --border-color: #e5e7eb; /* Light border */
    }

    /* Dark mode variables */
    [data-theme="dark"] {
        --primary-color: #60a5fa; /* Lighter blue */
        --secondary-color: #a855f7; /* Lighter purple */
        --background-color: #1f2937; /* Dark background */
        --card-bg: #374151; /* Dark card background */
        --text-color: #f3f4f6; /* Light text */
        --border-color: #4b5563; /* Darker border */
    }

    body {
        margin: 0;
        font-family: 'Poppins', sans-serif;
        background-color: var(--background-color);
        color: var(--text-color);
        transition: all 0.3s ease;
    }

    /* Modern header with glassmorphism effect */
    header {
        background: rgba(59, 130, 246, 0.1);
        backdrop-filter: blur(10px);
        padding: 2rem;
        position: sticky;
        top: 0;
        z-index: 100;
        border-bottom: 1px solid var(--border-color);
    }

    .header-content {
        max-width: 1200px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
    }

    h1 {
        font-size: 2.5rem;
        margin: 0;
        background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    /* Modern button styles */
    .btn {
        padding: 0.75rem 1.5rem;
        border: none;
        border-radius: 0.5rem;
        background: var(--primary-color);
        color: white;
        font-weight: 500;
        cursor: pointer;
        transition: transform 0.2s, box-shadow 0.2s;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }

    /* Section layout */
    .section {
        max-width: 1400px;
        margin: 2rem auto;
        padding: 1rem;
    }

    .section h2 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        padding-bottom: 0.5rem;
        border-bottom: 2px solid var(--primary-color);
        display: inline-block;
    }

    /* Modern card grid layout */
    .container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 1.5rem;
        padding: 1rem;
    }

    /* Elegant card design */
    .card {
        background: var(--card-bg);
        border-radius: 1rem;
        padding: 1rem;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        transition: all 0.3s ease;
        border: 1px solid var(--border-color);
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
        position: relative;
    }

    .card:hover {
        transform: translateY(-5px);
        box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
    }

    /* Card content styles */
    .card span {
        font-weight: 600;
        font-size: 1.1rem;
    }

    .card a {
        text-decoration: none;
        color: var(--primary-color);
        font-weight: 500;
        transition: color 0.2s;
    }

    .card a:hover {
        color: var(--secondary-color);
    }

    /* Modern form controls */
    .controls {
        background: var(--card-bg);
        padding: 1rem;
        border-radius: 0.5rem;
        display: flex;
        gap: 0.5rem;
        flex-wrap: wrap;
        justify-content: center;
        margin-top: 1rem;
    }

    .controls input {
        padding: 0.75rem 1rem;
        border: 1px solid var(--border-color);
        border-radius: 0.5rem;
        background: var(--background-color);
        color: var(--text-color);
        min-width: 200px;
    }

    /* Tooltip redesign */
    .tooltip {
        position: absolute;
        bottom: 100%;
        left: 0;
        background: var(--card-bg);
        padding: 1rem;
        border-radius: 0.5rem;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        border: 1px solid var(--border-color);
        width: 250px;
        z-index: 10;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease;
    }

    .card:hover .tooltip {
        opacity: 1;
        visibility: visible;
        transform: translateY(-10px);
    }

    /* Status messages */
    .import-status {
        position: fixed;
        top: 2rem;
        right: 2rem;
        padding: 1rem 2rem;
        border-radius: 0.5rem;
        color: white;
        font-weight: 500;
        z-index: 1000;
        transform: translateX(100%);
        animation: slideIn 0.3s forwards;
    }

    @keyframes slideIn {
        to {
            transform: translateX(0);
        }
    }

    /* Notes panel redesign */
    .notes-panel {
        background: var(--card-bg);
        border-radius: 1rem;
        padding: 1.5rem;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        max-width: 800px;
        margin: 2rem auto;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 1000;
        width: 90%;
    }

    .notes-panel textarea {
        width: 100%;
        min-height: 200px;
        padding: 1rem;
        border-radius: 0.5rem;
        border: 1px solid var(--border-color);
        background: var(--background-color);
        color: var(--text-color);
        font-family: 'Poppins', sans-serif;
        resize: vertical;
        margin-bottom: 1rem;
    }

    .notes-controls {
        display: flex;
        gap: 1rem;
        justify-content: flex-end;
    }

    .notes-controls .btn {
        padding: 0.5rem 1rem;
    }

    /* Responsive design */
    @media (max-width: 768px) {
        .container {
            grid-template-columns: 1fr;
        }

        .controls {
            flex-direction: column;
        }

        .controls input,
        .controls button {
            width: 100%;
        }
    }

    /* Search bar styles */
    .search-container {
        margin: 1rem auto;
        max-width: 600px;
        display: flex;
        gap: 1rem;
        padding: 1rem;
    }

    .search-input {
        flex: 1;
        padding: 0.75rem;
        border-radius: 0.5rem;
        border: 1px solid var(--border-color);
        background: var(--card-bg);
        color: var(--text-color);
    }

    /* Category tag styles */
    .category-tag {
        font-size: 0.8rem;
        padding: 0.25rem 0.5rem;
        border-radius: 1rem;
        margin-right: 0.5rem;
        color: white;
    }

    /* Sort controls */
    .sort-controls {
        display: flex;
        gap: 1rem;
        margin: 1rem;
        justify-content: center;
    }

    /* Favorite button */
    .favorite-btn {
        background: none;
        border: none;
        font-size: 1.2rem;
        cursor: pointer;
        color: #gray;
        transition: color 0.3s;
    }

    .favorite-btn.active {
        color: #ffd700;
    }

    /* Copy button */
    .copy-btn {
        padding: 0.25rem 0.5rem;
        background: var(--primary-color);
        color: white;
        border: none;
        border-radius: 0.25rem;
        cursor: pointer;
        font-size: 0.8rem;
    }

    .copy-btn:hover {
        background: var(--secondary-color);
    }

    /* Section creation styles */
    .section-creation {
        max-width: 600px;
        margin: 2rem auto;
        display: flex;
        flex-direction: column;
        gap: 1rem;
        padding: 1rem;
        background: var(--card-bg);
        border-radius: 0.5rem;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    .section-creation input {
        padding: 0.75rem;
        border-radius: 0.5rem;
        border: 1px solid var(--border-color);
        background: var(--background-color);
        color: var(--text-color);
    }

    /* Add this CSS for the delete section button */
    .section-header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 1rem;
    }

    .delete-section-btn {
        background: #ef4444;
        color: white;
        border: none;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    .delete-section-btn:hover {
        background: #dc2626;
    }

    .notes-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 1rem;
    }

    .notes-header h3 {
        margin: 0;
    }

    .notes-header .btn {
        background: #ef4444;
        color: white;
        border: none;
        padding: 0.5rem 1rem;
        border-radius: 0.5rem;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    .notes-header .btn:hover {
        background: #dc2626;
    }

    
  </style>
</head>
<body data-theme="dark">
    <header>
	 
	<center>
	<h3>QA Test Environments</h3>
       <a class="btn btn-primary custom-bg-color-9" href="file:///C:/Users/negesu01/OneDrive%20-%20Reed%20Elsevier%20Group%20ICO%20Reed%20Elsevier%20Inc/Desktop/Postman&amp;ReadyAPI/BridgerNavigationTool/DirectoryQA/QA-TestEnv.html" role="button" style="background-color: #35b0e5; color: #333; border: none; border-radius: 5px; padding: 3px 8px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: background-color 0.3s, transform 0.3s; text-decoration: none;" target="_blank">OG-Bridger-Test-Environments 🛠️🚀🔍</a>
			<p> </p>
	            <a class="btn btn-primary custom-bg-color-9" href="file:///C:/Users/negesu01/OneDrive%20-%20Reed%20Elsevier%20Group%20ICO%20Reed%20Elsevier%20Inc/Desktop/Postman&amp;ReadyAPI/BridgerNavigationTool/DirectoryQA/BridgerInsightWiki.html" role="button" style="background-color: #35b0e5; color: #333; border: none; border-radius: 5px; padding: 3px 8px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: background-color 0.3s, transform 0.3s; text-decoration: none;" target="_blank">BridgerInsightWiki 🛠️🚀🔍</a>
			  <p> </p>
			   <a class="btn btn-primary custom-bg-color-9" href="file:///C:/Users/negesu01/OneDrive%20-%20Reed%20Elsevier%20Group%20ICO%20Reed%20Elsevier%20Inc/Desktop/Postman&amp;ReadyAPI/BridgerNavigationTool/DirectoryQA/QA-MasterLinkManager.html" role="button" style="background-color: #35b0e5; color: #333; border: none; border-radius: 5px; padding: 3px 8px; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: background-color 0.3s, transform 0.3s; text-decoration: none;" target="_blank">OG-Bridger-QA 🛠️🚀🔍</a>
		 </center>
		 <button id="toggle-dark-mode" class="btn" onclick="toggleDarkMode()">Dark Mode</button>
    </header>
    <div class="section-creation">
        <h2>Create New Section</h2>
        <input type="text" id="new-section-name" placeholder="Enter section name...">
        <button class="btn" onclick="addNewSection()">Add Section</button>
    </div>

    <div class="random-generator">
        <h3>Random Client, Username, and Password Generator</h3>
        <div class="controls">
            <button class="btn" onclick="generateRandomClient()">Generate Random Client</button>
            <input type="text" id="random-client" placeholder="Random Client Name" readonly="">
        </div>
        <div class="controls">
            <button class="btn" onclick="generateRandomUsername()">Generate Random Username</button>
            <input type="text" id="random-username" placeholder="Random Username" readonly="">
        </div>
        <div class="controls">
            <button class="btn" onclick="generateRandomPassword()">Generate Random Password</button>
            <input type="text" id="random-password" placeholder="Random Password" readonly="">
        </div>

    <div class="search-container">
        <input type="text" class="search-input" placeholder="Search cards..." onkeyup="filterCards(this.value)">
        <select onchange="sortCards(this.value)" class="btn">
            <option value="name">Sort by Name</option>
            <option value="date">Sort by Date</option>
            <option value="category">Sort by Category</option>
        </select>
    </div>

    <div class="import-export">
        <input type="file" id="import-file" accept=".json" onchange="importData(event)">
    </div>

    <div class="controls">
        <button onclick="exportData()">Export Data</button>
        <button onclick="toggleNotes()" class="notes-btn">Toggle Notes</button>
    </div>

    <!-- Sections -->
    <div class="section" id="general-section">
        <h2>DEV:QA326 🧪</h2>
        <div class="container" id="general-container"><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM creds</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'EM creds')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/xgauth/Account/Logon?returnUrl=/XgApp/Enterprise/Client/4392&amp;messageId=3" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'EM creds')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-EM creds-client" value="629684">
                        <button class="copy-btn" onclick="copyToClipboard('629684')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-EM creds-userid" value="snadmin1 ">
                        <button class="copy-btn" onclick="copyToClipboard('snadmin1 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-EM creds-password" value="P@ssword-11">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssword-11')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'EM creds')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>SecurityCheckCode</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'SecurityCheckCode')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/xgauth/Account/Logon?returnUrl=/XgApp/Enterprise/Client/4392&amp;messageId=3" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'SecurityCheckCode')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-SecurityCheckCode-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-SecurityCheckCode-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-SecurityCheckCode-password" value="856854">
                        <button class="copy-btn" onclick="copyToClipboard('856854')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'SecurityCheckCode')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Client - MultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Client - MultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Client - MultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Client - MultiDB-client" value="autoSQLServer2">
                        <button class="copy-btn" onclick="copyToClipboard('autoSQLServer2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Client - MultiDB-userid" value="Admin1221">
                        <button class="copy-btn" onclick="copyToClipboard('Admin1221')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Client - MultiDB-password" value="Welcome123~!!!@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome123~!!!@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Client - MultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Client 2: MultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Client 2: MultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Client 2: MultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Client 2: MultiDB-client" value="surafal33Multidb ">
                        <button class="copy-btn" onclick="copyToClipboard('surafal33Multidb ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Client 2: MultiDB-userid" value="stester13 ">
                        <button class="copy-btn" onclick="copyToClipboard('stester13 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Client 2: MultiDB-password" value="Welcome123~!!!@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome123~!!!@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Client 2: MultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ComplianceOfficer-MultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'ComplianceOfficer-MultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'ComplianceOfficer-MultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-ComplianceOfficer-MultiDB-client" value="autoSQLServer2">
                        <button class="copy-btn" onclick="copyToClipboard('autoSQLServer2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-ComplianceOfficer-MultiDB-userid" value="ComplianceTest1">
                        <button class="copy-btn" onclick="copyToClipboard('ComplianceTest1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-ComplianceOfficer-MultiDB-password" value="allnight8S@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'ComplianceOfficer-MultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ERF-TestClient - SysDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'ERF-TestClient - SysDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'ERF-TestClient - SysDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-ERF-TestClient - SysDB-client" value="TestERFPDS2025">
                        <button class="copy-btn" onclick="copyToClipboard('TestERFPDS2025')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-ERF-TestClient - SysDB-userid" value="PDSERF25">
                        <button class="copy-btn" onclick="copyToClipboard('PDSERF25')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-ERF-TestClient - SysDB-password" value="P@ssword-11">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssword-11')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'ERF-TestClient - SysDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ERF-MultiDBClient</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'ERF-MultiDBClient')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'ERF-MultiDBClient')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-ERF-MultiDBClient-client" value="ERFMultiDB2">
                        <button class="copy-btn" onclick="copyToClipboard('ERFMultiDB2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-ERF-MultiDBClient-userid" value="multDBERF2">
                        <button class="copy-btn" onclick="copyToClipboard('multDBERF2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-ERF-MultiDBClient-password" value="P@ssword-11">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssword-11')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'ERF-MultiDBClient')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129590" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Non-ERF-Sysdb</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Non-ERF-Sysdb')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Non-ERF-Sysdb')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Non-ERF-Sysdb-client" value="NonERFTestClient2">
                        <button class="copy-btn" onclick="copyToClipboard('NonERFTestClient2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Non-ERF-Sysdb-userid" value="nonERF2025">
                        <button class="copy-btn" onclick="copyToClipboard('nonERF2025')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Non-ERF-Sysdb-password" value="Welcome123~!!!@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome123~!!!@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Non-ERF-Sysdb')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>NonERF-MultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'NonERF-MultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'NonERF-MultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-NonERF-MultiDB-client" value="nonERFMultidb2025">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFMultidb2025')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-NonERF-MultiDB-userid" value="nonERFMultiDB2">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFMultiDB2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-NonERF-MultiDB-password" value="allnight8S@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'NonERF-MultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Kibana Logs')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/login" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Kibana Logs')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Kibana Logs-client" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Kibana Logs-userid" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Kibana Logs-password" value="AD Auth">
                        <button class="copy-btn" onclick="copyToClipboard('AD Auth')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Kibana Logs')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>📄 QA326 Log Files</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', '📄 QA326 Log Files')">
                        ⭐
                    </button>
                </div>
                <a href="file:///\\alawtbrg326.risk.regn.net/Deployment/Logs" target="_blank">Visit</a>
                <button onclick="removeCard('general', '📄 QA326 Log Files')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-📄 QA326 Log Files-client" value="alawtbrg326.risk.regn.net">
                        <button class="copy-btn" onclick="copyToClipboard('alawtbrg326.risk.regn.net')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-📄 QA326 Log Files-userid" value="RISK\Negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('RISK\Negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-📄 QA326 Log Files-password" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', '📄 QA326 Log Files')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI pipline: Azure - Dev</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'ReadyAPI pipline: Azure - Dev')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/AZURE-DEV.yml" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'ReadyAPI pipline: Azure - Dev')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-ReadyAPI pipline: Azure - Dev-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-ReadyAPI pipline: Azure - Dev-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-ReadyAPI pipline: Azure - Dev-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'ReadyAPI pipline: Azure - Dev')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-DEV-EM</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'AZ-DEV-EM')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/xgauth" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'AZ-DEV-EM')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-AZ-DEV-EM-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-AZ-DEV-EM-userid" value="sysSurafal1">
                        <button class="copy-btn" onclick="copyToClipboard('sysSurafal1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-AZ-DEV-EM-password" value="Abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('Abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'AZ-DEV-EM')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(255, 111, 105);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-ERF-SysDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'AZ-ERF-SysDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/xgauth" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'AZ-ERF-SysDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-AZ-ERF-SysDB-client" value="SurafalERFsysdb2">
                        <button class="copy-btn" onclick="copyToClipboard('SurafalERFsysdb2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-AZ-ERF-SysDB-userid" value="erfsysdb1">
                        <button class="copy-btn" onclick="copyToClipboard('erfsysdb1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-AZ-ERF-SysDB-password" value="Abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('Abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'AZ-ERF-SysDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-ERF-Multidb</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'AZ-ERF-Multidb')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/xgauth" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'AZ-ERF-Multidb')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-AZ-ERF-Multidb-client" value="lmultidbERF2">
                        <button class="copy-btn" onclick="copyToClipboard('lmultidbERF2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-AZ-ERF-Multidb-userid" value="sysMultidb2">
                        <button class="copy-btn" onclick="copyToClipboard('sysMultidb2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-AZ-ERF-Multidb-password" value="Abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('Abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'AZ-ERF-Multidb')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-Multidb-NonERF</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'AZ-Multidb-NonERF')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/xgauth" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'AZ-Multidb-NonERF')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-AZ-Multidb-NonERF-client" value="nonERFmutlidb2">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFmutlidb2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-AZ-Multidb-NonERF-userid" value="multidbnonERF2">
                        <button class="copy-btn" onclick="copyToClipboard('multidbnonERF2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-AZ-Multidb-NonERF-password" value="Abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('Abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'AZ-Multidb-NonERF')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-NonERF-sysdb-SAML</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'AZ-NonERF-sysdb-SAML')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/XgApp" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'AZ-NonERF-sysdb-SAML')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-AZ-NonERF-sysdb-SAML-client" value="nonERFsysdb2">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFsysdb2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-AZ-NonERF-sysdb-SAML-userid" value="sysdbnonERF1">
                        <button class="copy-btn" onclick="copyToClipboard('sysdbnonERF1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-AZ-NonERF-sysdb-SAML-password" value="Abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('Abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'AZ-NonERF-sysdb-SAML')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129591" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Kibana Logs')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-dev.azure.lnrsg.io/s/team-bridger/app/r/s/eAz7I" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Kibana Logs')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Kibana Logs-client" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Kibana Logs-userid" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Kibana Logs-password" value="AD Auth">
                        <button class="copy-btn" onclick="copyToClipboard('AD Auth')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Kibana Logs')">Save</button>
                </div>
            </div><div class="card" data-date="1741782191919" data-category="" style="background-color: rgb(161, 98, 7);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Deployment Status Check</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Deployment Status Check')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-xg5-helm/actions/runs/13802602118" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Deployment Status Check')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Deployment Status Check-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Deployment Status Check-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Deployment Status Check-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Deployment Status Check')">Save</button>
                </div>
            </div><div class="card" data-date="1742240406183" data-category="" style="background-color: rgb(161, 98, 7);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Employee - ID:00000629684</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'Employee - ID:00000629684')">
                        ⭐
                    </button>
                </div>
                <a href="https://wd3.myworkday.com/relx/d/inst/1$37/247$76525.htmld?metadataEntryPoint=%2Frelx%2Flearning%2Fdiscover#TABTASKID=2998%246445" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'Employee - ID:00000629684')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-Employee - ID:00000629684-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-Employee - ID:00000629684-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-Employee - ID:00000629684-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'Employee - ID:00000629684')">Save</button>
                </div>
            </div><div class="card" data-date="1742481730682" data-category="" style="background-color: rgb(139, 92, 246);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>SAML-Manage</span>
                    <button class="favorite-btn " onclick="toggleFavorite('general', 'SAML-Manage')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/IdpSaml" target="_blank">Visit</a>
                <button onclick="removeCard('general', 'SAML-Manage')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="general-SAML-Manage-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="general-SAML-Manage-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="general-SAML-Manage-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('general', 'SAML-Manage')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="general-name" placeholder="Card name...">
            <input type="url" id="general-url" placeholder="Card link...">
            <button onclick="addCard('general')">Add</button>
        </div>
    </div>

    <div class="section" id="development-section">
        <h2>Az:NonPROD:QA☁️</h2>
        <div class="container" id="development-container"><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM Login</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'EM Login')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'EM Login')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-EM Login-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-EM Login-userid" value="syssurafal1 ">
                        <button class="copy-btn" onclick="copyToClipboard('syssurafal1 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-EM Login-password" value="abc123$$@@">
                        <button class="copy-btn" onclick="copyToClipboard('abc123$$@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'EM Login')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Log</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'Kibana Log')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-dev.azure.lnrsg.io/login?next=%2F" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'Kibana Log')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-Kibana Log-client" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-Kibana Log-userid" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-Kibana Log-password" value="AD Auth">
                        <button class="copy-btn" onclick="copyToClipboard('AD Auth')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'Kibana Log')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>DataBridge Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'DataBridge Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'DataBridge Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-DataBridge Client-client" value="LNDataBridge ">
                        <button class="copy-btn" onclick="copyToClipboard('LNDataBridge ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-DataBridge Client-userid" value="surafeldatabridge2 ">
                        <button class="copy-btn" onclick="copyToClipboard('surafeldatabridge2 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-DataBridge Client-password" value="allnight87S@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'DataBridge Client')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM Server Administrator</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'EM Server Administrator')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'EM Server Administrator')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-EM Server Administrator-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-EM Server Administrator-userid" value="admin282 ">
                        <button class="copy-btn" onclick="copyToClipboard('admin282 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-EM Server Administrator-password" value="allnight8S@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'EM Server Administrator')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM: Support Administrator</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'EM: Support Administrator')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'EM: Support Administrator')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-EM: Support Administrator-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-EM: Support Administrator-userid" value="supportAdmin1234">
                        <button class="copy-btn" onclick="copyToClipboard('supportAdmin1234')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-EM: Support Administrator-password" value="allnight8S@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'EM: Support Administrator')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>NonERFsysDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'NonERFsysDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'NonERFsysDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-NonERFsysDB-client" value="NonERFClientSysdb">
                        <button class="copy-btn" onclick="copyToClipboard('NonERFClientSysdb')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-NonERFsysDB-userid" value="nonERFTest1sysdb">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFTest1sysdb')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-NonERFsysDB-password" value="P@ssw0rd123@@">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssw0rd123@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'NonERFsysDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>NonERFMultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'NonERFMultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'NonERFMultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-NonERFMultiDB-client" value="nonERFMultidB">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFMultidB')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-NonERFMultiDB-userid" value="nonERFMultiDBTest1">
                        <button class="copy-btn" onclick="copyToClipboard('nonERFMultiDBTest1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-NonERFMultiDB-password" value="P@ssw0rd123@">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssw0rd123@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'NonERFMultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ERFsysDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ERFsysDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ERFsysDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ERFsysDB-client" value="ERFsysDB">
                        <button class="copy-btn" onclick="copyToClipboard('ERFsysDB')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ERFsysDB-userid" value="sysDBERF2">
                        <button class="copy-btn" onclick="copyToClipboard('sysDBERF2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ERFsysDB-password" value="P@ssw0rd123@">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssw0rd123@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ERFsysDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ERFMultiDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ERFMultiDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ERFMultiDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ERFMultiDB-client" value="ERFmultidbDBclient">
                        <button class="copy-btn" onclick="copyToClipboard('ERFmultidbDBclient')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ERFMultiDB-userid" value="ERFsysDBclient">
                        <button class="copy-btn" onclick="copyToClipboard('ERFsysDBclient')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ERFMultiDB-password" value="P@ssw0rd123@">
                        <button class="copy-btn" onclick="copyToClipboard('P@ssw0rd123@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ERFMultiDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM-Support Administrator</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'EM-Support Administrator')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'EM-Support Administrator')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-EM-Support Administrator-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-EM-Support Administrator-userid" value="supportAdmin1234 ">
                        <button class="copy-btn" onclick="copyToClipboard('supportAdmin1234 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-EM-Support Administrator-password" value="allnight8S@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'EM-Support Administrator')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM-server Administrator</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'EM-server Administrator')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'EM-server Administrator')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-EM-server Administrator-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-EM-server Administrator-userid" value="admin282 ">
                        <button class="copy-btn" onclick="copyToClipboard('admin282 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-EM-server Administrator-password" value="allnight8S@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'EM-server Administrator')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI pipline:Azure - NonProd</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI pipline:Azure - NonProd')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/AZURE-NONPROD.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI pipline:Azure - NonProd')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI pipline:Azure - NonProd-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI pipline:Azure - NonProd-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI pipline:Azure - NonProd-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI pipline:Azure - NonProd')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI-Azure - NonProd Regression</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI-Azure - NonProd Regression')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/Azure-NONPROD-REGRESSION.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI-Azure - NonProd Regression')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI-Azure - NonProd Regression-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI-Azure - NonProd Regression-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI-Azure - NonProd Regression-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI-Azure - NonProd Regression')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI: Azure - NonProd WCO Security Scan</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI: Azure - NonProd WCO Security Scan')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/SECURITY-WCO.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI: Azure - NonProd WCO Security Scan')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI: Azure - NonProd WCO Security Scan-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI: Azure - NonProd WCO Security Scan-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI: Azure - NonProd WCO Security Scan-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI: Azure - NonProd WCO Security Scan')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(20, 184, 166);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI: NonProd BDDS Security Scan</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI: NonProd BDDS Security Scan')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/SECURITY-BDDS.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI: NonProd BDDS Security Scan')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI: NonProd BDDS Security Scan-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI: NonProd BDDS Security Scan-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI: NonProd BDDS Security Scan-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI: NonProd BDDS Security Scan')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129592" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/SECURITY-XG5.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI - PIpline :Azure - NonProd XG5 Security Scan')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : SSC Security Scan</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'ReadyAPI - PIpline : SSC Security Scan')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/SECURITY-SSC.yml" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'ReadyAPI - PIpline : SSC Security Scan')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-ReadyAPI - PIpline : SSC Security Scan-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-ReadyAPI - PIpline : SSC Security Scan-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-ReadyAPI - PIpline : SSC Security Scan-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'ReadyAPI - PIpline : SSC Security Scan')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>UI AUtomation Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'UI AUtomation Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/xgauth/Account/Logon?returnUrl=&amp;messageId=4" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'UI AUtomation Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-UI AUtomation Client-client" value="UITest2">
                        <button class="copy-btn" onclick="copyToClipboard('UITest2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-UI AUtomation Client-userid" value="Administrator1">
                        <button class="copy-btn" onclick="copyToClipboard('Administrator1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-UI AUtomation Client-password" value="allnight87S!@#@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'UI AUtomation Client')">Save</button>
                </div>
            </div><div class="card" data-date="1741357530085" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Exact</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'Kibana Exact')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-dev.azure.lnrsg.io/s/team-bridger/app/r/s/eAz7I" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'Kibana Exact')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-Kibana Exact-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-Kibana Exact-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-Kibana Exact-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'Kibana Exact')">Save</button>
                </div>
            </div><div class="card" data-date="1741616290566" data-category="" style="background-color: rgb(83, 91, 45);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>UI Automation Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'UI Automation Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgApp/Enterprise/Client" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'UI Automation Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-UI Automation Client-client" value="Administrator1">
                        <button class="copy-btn" onclick="copyToClipboard('Administrator1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-UI Automation Client-userid" value="syssurafal1">
                        <button class="copy-btn" onclick="copyToClipboard('syssurafal1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-UI Automation Client-password" value="abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'UI Automation Client')">Save</button>
                </div>
            </div><div class="card" data-date="1741882861984" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana - SSC/CSL</span>
                    <button class="favorite-btn " onclick="toggleFavorite('development', 'Kibana - SSC/CSL')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-dev.azure.lnrsg.io/s/team-bridger/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:60000),time:(from:now-24h%2Fh,to:now))&amp;_a=(columns:!(fields.type,fields.env,Message),dataSource:(dataViewId:'5a4bdccf-bbc1-49af-8ae3-38dc5f1ade96',type:dataView),filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'5a4bdccf-bbc1-49af-8ae3-38dc5f1ade96',key:fields.env,negate:!f,params:(query:azurenonprod),type:phrase),query:(match_phrase:(fields.env:azurenonprod))),('$state':(store:appState),meta:(alias:!n,disabled:!f,field:Categories,index:'5a4bdccf-bbc1-49af-8ae3-38dc5f1ade96',key:Categories,negate:!f,params:(query:Error),type:phrase),query:(match_phrase:(Categories:Error))),('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'5a4bdccf-bbc1-49af-8ae3-38dc5f1ade96',key:fields.type,negate:!f,params:(query:wlm_svc),type:phrase),query:(match_phrase:(fields.type:wlm_svc)))),grid:(columns:(fields.env:(width:223),fields.type:(width:123))),interval:auto,query:(language:kuery,query:''),sort:!(!('@timestamp',desc)))" target="_blank">Visit</a>
                <button onclick="removeCard('development', 'Kibana - SSC/CSL')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="development-Kibana - SSC/CSL-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="development-Kibana - SSC/CSL-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="development-Kibana - SSC/CSL-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('development', 'Kibana - SSC/CSL')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="development-name" placeholder="Card name...">
            <input type="url" id="development-url" placeholder="Card link...">
            <button onclick="addCard('development')">Add</button>
        </div>
    </div>

    <div class="section" id="design-section">
        <h2>U.S. Staging 🏦</h2>
        <div class="container" id="design-container"><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US-Stag-sysDB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('design', 'US-Stag-sysDB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridgerstaging.lexisnexis.com" target="_blank">Visit</a>
                <button onclick="removeCard('design', 'US-Stag-sysDB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="design-US-Stag-sysDB-client" value="LNSNegereTest">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereTest')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="design-US-Stag-sysDB-userid" value="SNegere15">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere15')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="design-US-Stag-sysDB-password" value="password-123@">
                        <button class="copy-btn" onclick="copyToClipboard('password-123@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('design', 'US-Stag-sysDB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Log</span>
                    <button class="favorite-btn " onclick="toggleFavorite('design', 'Kibana Log')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/login" target="_blank">Visit</a>
                <button onclick="removeCard('design', 'Kibana Log')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="design-Kibana Log-client" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="design-Kibana Log-userid" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="design-Kibana Log-password" value="AD Auth">
                        <button class="copy-btn" onclick="copyToClipboard('AD Auth')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('design', 'Kibana Log')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US Stage Smoke Test - Pipline</span>
                    <button class="favorite-btn " onclick="toggleFavorite('design', 'US Stage Smoke Test - Pipline')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/us-stage-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('design', 'US Stage Smoke Test - Pipline')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="design-US Stage Smoke Test - Pipline-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="design-US Stage Smoke Test - Pipline-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="design-US Stage Smoke Test - Pipline-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('design', 'US Stage Smoke Test - Pipline')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : US - Staging Active</span>
                    <button class="favorite-btn " onclick="toggleFavorite('design', 'ReadyAPI - PIpline : US - Staging Active')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/STAGING-US%20ACTIVE.yml" target="_blank">Visit</a>
                <button onclick="removeCard('design', 'ReadyAPI - PIpline : US - Staging Active')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="design-ReadyAPI - PIpline : US - Staging Active-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="design-ReadyAPI - PIpline : US - Staging Active-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="design-ReadyAPI - PIpline : US - Staging Active-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('design', 'ReadyAPI - PIpline : US - Staging Active')">Save</button>
                </div>
            </div><div class="card" data-date="1742481685762" data-category="" style="background-color: rgb(69, 183, 209);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>SAML - Manage</span>
                    <button class="favorite-btn " onclick="toggleFavorite('design', 'SAML - Manage')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawtbrg326.risk.regn.net/IdpSaml" target="_blank">Visit</a>
                <button onclick="removeCard('design', 'SAML - Manage')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="design-SAML - Manage-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="design-SAML - Manage-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="design-SAML - Manage-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('design', 'SAML - Manage')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="design-name" placeholder="Card name...">
            <input type="url" id="design-url" placeholder="Card link...">
            <button onclick="addCard('design')">Add</button>
        </div>
    </div>

    <div class="section" id="Green-section">
        <h2>U.S. Staging - Green</h2>
        <div class="container" id="Green-container"><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline :US - Staging Green</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Green', 'ReadyAPI - PIpline :US - Staging Green')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/STAGING-US%20GREEN.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Green', 'ReadyAPI - PIpline :US - Staging Green')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Green-ReadyAPI - PIpline :US - Staging Green-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Green-ReadyAPI - PIpline :US - Staging Green-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Green-ReadyAPI - PIpline :US - Staging Green-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Green', 'ReadyAPI - PIpline :US - Staging Green')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="Green-name" placeholder="Card name...">
            <input type="url" id="Green-url" placeholder="Card link...">
            <button onclick="addCard('Green')">Add</button>
        </div>
    </div>

    <div class="section" id="Blue-section">
        <h2>U.S. Staging - Blue</h2>
        <div class="container" id="Blue-container"><div class="card" data-date="1742656129593" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : US - Staging Blue</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Blue', 'ReadyAPI - PIpline : US - Staging Blue')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/STAGING-US%20BLUE.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Blue', 'ReadyAPI - PIpline : US - Staging Blue')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Blue-ReadyAPI - PIpline : US - Staging Blue-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Blue-ReadyAPI - PIpline : US - Staging Blue-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Blue-ReadyAPI - PIpline : US - Staging Blue-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Blue', 'ReadyAPI - PIpline : US - Staging Blue')">Save</button>
                </div>
            </div><div class="card" data-date="1740754129030" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US  Staging - Blue</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Blue', 'US  Staging - Blue')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridgerstagingblue.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('Blue', 'US  Staging - Blue')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Blue-US  Staging - Blue-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Blue-US  Staging - Blue-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Blue-US  Staging - Blue-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Blue', 'US  Staging - Blue')">Save</button>
                </div>
            </div><div class="card" data-date="1740754509824" data-category="" style="background-color: rgb(255, 111, 105);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Smoke Test- Blue</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Blue', 'Smoke Test- Blue')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/us-stage-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Blue', 'Smoke Test- Blue')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Blue-Smoke Test- Blue-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Blue-Smoke Test- Blue-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Blue-Smoke Test- Blue-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Blue', 'Smoke Test- Blue')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="Blue-name" placeholder="Card name...">
            <input type="url" id="Blue-url" placeholder="Card link...">
            <button onclick="addCard('Blue')">Add</button>
        </div>
    </div>

    <div class="section" id="META-section">
        <h2>META MPC</h2>
        <div class="container" id="META-container"><div class="card" data-date="1740422355200" data-category="" style="background-color: rgb(45, 51, 91);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>META-Green</span>
                    <button class="favorite-btn " onclick="toggleFavorite('META', 'META-Green')">
                        ⭐
                    </button>
                </div>
                <a href="https://ma1.brmpc.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('META', 'META-Green')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="META-META-Green-client" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="META-META-Green-userid" value="san483cd">
                        <button class="copy-btn" onclick="copyToClipboard('san483cd')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="META-META-Green-password" value="password1!2@">
                        <button class="copy-btn" onclick="copyToClipboard('password1!2@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('META', 'META-Green')">Save</button>
                </div>
            </div><div class="card" data-date="1740422468217" data-category="" style="background-color: rgb(88, 140, 126);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Meta-Blue</span>
                    <button class="favorite-btn " onclick="toggleFavorite('META', 'Meta-Blue')">
                        ⭐
                    </button>
                </div>
                <a href="https://ma0.brmpc.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('META', 'Meta-Blue')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="META-Meta-Blue-client" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="META-Meta-Blue-userid" value="san483cd">
                        <button class="copy-btn" onclick="copyToClipboard('san483cd')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="META-Meta-Blue-password" value="password1!2@">
                        <button class="copy-btn" onclick="copyToClipboard('password1!2@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('META', 'Meta-Blue')">Save</button>
                </div>
            </div><div class="card" data-date="1740422758012" data-category="" style="background-color: rgb(161, 98, 7);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>META-Green-SFTP-AB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('META', 'META-Green-SFTP-AB')">
                        ⭐
                    </button>
                </div>
                <a href="https://ma1.brmpc.lexisnexisrisk.com/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('META', 'META-Green-SFTP-AB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="META-META-Green-SFTP-AB-client" value="sftp1.ma.brmpc.lexisnexisrisk.net">
                        <button class="copy-btn" onclick="copyToClipboard('sftp1.ma.brmpc.lexisnexisrisk.net')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="META-META-Green-SFTP-AB-userid" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="META-META-Green-SFTP-AB-password" value=".PSS91plM%%D#">
                        <button class="copy-btn" onclick="copyToClipboard('.PSS91plM%%D#')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('META', 'META-Green-SFTP-AB')">Save</button>
                </div>
            </div><div class="card" data-date="1740422821787" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>META-Blue-SFTP -AB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('META', 'META-Blue-SFTP -AB')">
                        ⭐
                    </button>
                </div>
                <a href="https://ma0.brmpc.lexisnexisrisk.com/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('META', 'META-Blue-SFTP -AB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="META-META-Blue-SFTP -AB-client" value="sftp0.ma.brmpc.lexisnexisrisk.net">
                        <button class="copy-btn" onclick="copyToClipboard('sftp0.ma.brmpc.lexisnexisrisk.net')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="META-META-Blue-SFTP -AB-userid" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="META-META-Blue-SFTP -AB-password" value=".PSS91plM%%D#">
                        <button class="copy-btn" onclick="copyToClipboard('.PSS91plM%%D#')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('META', 'META-Blue-SFTP -AB')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="META-name" placeholder="Card name...">
            <input type="url" id="META-url" placeholder="Card link...">
            <button onclick="addCard('META')">Add</button>
        </div>
    </div>

    <div class="section" id="Block-section">
        <h2>Block MPC </h2>
        <div class="container" id="Block-container"><div class="card" data-date="1740425423973" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Blue-Block</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'Blue-Block')">
                        ⭐
                    </button>
                </div>
                <a href="https://bk0.brmpc.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'Blue-Block')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-Blue-Block-client" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-Blue-Block-userid" value="san483cd">
                        <button class="copy-btn" onclick="copyToClipboard('san483cd')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-Blue-Block-password" value="Password@2@">
                        <button class="copy-btn" onclick="copyToClipboard('Password@2@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'Blue-Block')">Save</button>
                </div>
            </div><div class="card" data-date="1740425474598" data-category="" style="background-color: rgb(83, 91, 45);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Green - Block</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'Green - Block')">
                        ⭐
                    </button>
                </div>
                <a href="https://bk1.brmpc.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'Green - Block')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-Green - Block-client" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-Green - Block-userid" value="san483cd">
                        <button class="copy-btn" onclick="copyToClipboard('san483cd')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-Green - Block-password" value="Password@2@">
                        <button class="copy-btn" onclick="copyToClipboard('Password@2@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'Green - Block')">Save</button>
                </div>
            </div><div class="card" data-date="1740425501447" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Smoke Test- Automation</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'Smoke Test- Automation')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/block-mpc-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'Smoke Test- Automation')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-Smoke Test- Automation-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-Smoke Test- Automation-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-Smoke Test- Automation-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'Smoke Test- Automation')">Save</button>
                </div>
            </div><div class="card" data-date="1740426713557" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Block MPC Smoke Test</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'Block MPC Smoke Test')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/block-mpc-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'Block MPC Smoke Test')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-Block MPC Smoke Test-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-Block MPC Smoke Test-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-Block MPC Smoke Test-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'Block MPC Smoke Test')">Save</button>
                </div>
            </div><div class="card" data-date="1740426746830" data-category="" style="background-color: rgb(150, 206, 180);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>API:Meta - Blue</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'API:Meta - Blue')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/BLUE-BLOCK.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'API:Meta - Blue')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-API:Meta - Blue-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-API:Meta - Blue-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-API:Meta - Blue-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'API:Meta - Blue')">Save</button>
                </div>
            </div><div class="card" data-date="1740426773131" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>API: Meta- Green</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'API: Meta- Green')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/GREEN-BLOCK.yml" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'API: Meta- Green')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-API: Meta- Green-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-API: Meta- Green-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-API: Meta- Green-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'API: Meta- Green')">Save</button>
                </div>
            </div><div class="card" data-date="1740427324411" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>BLOCK - SFTP IN</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Block', 'BLOCK - SFTP IN')">
                        ⭐
                    </button>
                </div>
                <a href="https://bk0.brmpc.lexisnexisrisk.com/xgauth" target="_blank">Visit</a>
                <button onclick="removeCard('Block', 'BLOCK - SFTP IN')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Block-BLOCK - SFTP IN-client" value="sftp.bk1.brmpc.lexisnexisrisk.com">
                        <button class="copy-btn" onclick="copyToClipboard('sftp.bk1.brmpc.lexisnexisrisk.com')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Block-BLOCK - SFTP IN-userid" value="LNEngineering">
                        <button class="copy-btn" onclick="copyToClipboard('LNEngineering')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Block-BLOCK - SFTP IN-password" value="3[uqe0z[D9#k">
                        <button class="copy-btn" onclick="copyToClipboard('3[uqe0z[D9#k')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Block', 'BLOCK - SFTP IN')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="Block-name" placeholder="Card name...">
            <input type="url" id="Block-url" placeholder="Card link...">
            <button onclick="addCard('Block')">Add</button>
        </div>
    </div>

    <div class="section" id="usPROD-section">
        <h2>U.S.PROD</h2>
        <div class="container" id="usPROD-container"><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US Prod</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'US Prod')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.com" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'US Prod')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-US Prod-client" value="LNSNegereUS ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUS ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-US Prod-userid" value="SNegere33 ">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere33 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-US Prod-password" value="Welcome1234!!@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234!!@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'US Prod')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Databridge Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'Databridge Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.com" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'Databridge Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-Databridge Client-client" value="sanwaarlnxg4 ">
                        <button class="copy-btn" onclick="copyToClipboard('sanwaarlnxg4 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-Databridge Client-userid" value="negeretest1">
                        <button class="copy-btn" onclick="copyToClipboard('negeretest1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-Databridge Client-password" value="password-1233@">
                        <button class="copy-btn" onclick="copyToClipboard('password-1233@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'Databridge Client')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Compliance User</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'Compliance User')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.com" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'Compliance User')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-Compliance User-client" value="LNSNegereUS ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUS ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-Compliance User-userid" value="LNSNegereUSC1 ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUSC1 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-Compliance User-password" value="allnight8S@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'Compliance User')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>MultiDB - Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'MultiDB - Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.com" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'MultiDB - Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-MultiDB - Client-client" value="SAnwaarLNMultiDB ">
                        <button class="copy-btn" onclick="copyToClipboard('SAnwaarLNMultiDB ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-MultiDB - Client-userid" value="surafaltest01 ">
                        <button class="copy-btn" onclick="copyToClipboard('surafaltest01 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-MultiDB - Client-password" value="Secure@1988@">
                        <button class="copy-btn" onclick="copyToClipboard('Secure@1988@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'MultiDB - Client')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US PROD Smoke Test - Piplines</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'US PROD Smoke Test - Piplines')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/us-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'US PROD Smoke Test - Piplines')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-US PROD Smoke Test - Piplines-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-US PROD Smoke Test - Piplines-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-US PROD Smoke Test - Piplines-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'US PROD Smoke Test - Piplines')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(161, 98, 7);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : US - Prod</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'ReadyAPI - PIpline : US - Prod')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/PROD-US.yml" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'ReadyAPI - PIpline : US - Prod')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-ReadyAPI - PIpline : US - Prod-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-ReadyAPI - PIpline : US - Prod-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-ReadyAPI - PIpline : US - Prod-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'ReadyAPI - PIpline : US - Prod')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : US - DR</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'ReadyAPI - PIpline : US - DR')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/DR-US.yml" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'ReadyAPI - PIpline : US - DR')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-ReadyAPI - PIpline : US - DR-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-ReadyAPI - PIpline : US - DR-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-ReadyAPI - PIpline : US - DR-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'ReadyAPI - PIpline : US - DR')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(20, 184, 166);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : US - Active</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'ReadyAPI - PIpline : US - Active')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/PRODACTIVE-US.yml" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'ReadyAPI - PIpline : US - Active')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-ReadyAPI - PIpline : US - Active-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-ReadyAPI - PIpline : US - Active-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-ReadyAPI - PIpline : US - Active-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'ReadyAPI - PIpline : US - Active')">Save</button>
                </div>
            </div><div class="card" data-date="1742237446547" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US - AZ Prod Kibana log</span>
                    <button class="favorite-btn " onclick="toggleFavorite('usPROD', 'US - AZ Prod Kibana log')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-prod.azure.lnrsg.io/s/team-bridger/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:60000),time:(from:now-2h,to:now))&amp;_a=(columns:!(message),dataSource:(dataViewId:'56a3c92e-3a11-490e-92f3-159dddf9efbd',type:dataView),filters:!(),hideChart:!f,interval:auto,query:(language:kuery,query:%22LNSNegereUS%22),sort:!(!('@timestamp',desc)))" target="_blank">Visit</a>
                <button onclick="removeCard('usPROD', 'US - AZ Prod Kibana log')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="usPROD-US - AZ Prod Kibana log-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="usPROD-US - AZ Prod Kibana log-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="usPROD-US - AZ Prod Kibana log-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('usPROD', 'US - AZ Prod Kibana log')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="usPROD-name" placeholder="Card name...">
            <input type="url" id="usPROD-url" placeholder="Card link...">
            <button onclick="addCard('usPROD')">Add</button>
        </div>
    </div>

    <div class="section" id="EuStaging-section">
        <h2>E.U.Staging</h2>
        <div class="container" id="EuStaging-container"><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU-Staging</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'EU-Staging')">
                        ⭐
                    </button>
                </div>
                <a href="https://staging.bridger.lexisnexis.eu/xgauth/" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'EU-Staging')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-EU-Staging-client" value="LNSNegereEU">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereEU')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-EU-Staging-userid" value="SNegere17">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere17')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-EU-Staging-password" value="Wednesday@123@">
                        <button class="copy-btn" onclick="copyToClipboard('Wednesday@123@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'EU-Staging')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>DR:Staging</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'DR:Staging')">
                        ⭐
                    </button>
                </div>
                <a href="https://dr.bridger.lexisnexis.eu/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'DR:Staging')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-DR:Staging-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-DR:Staging-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-DR:Staging-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'DR:Staging')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129595" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'Kibana Logs')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/login" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'Kibana Logs')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-Kibana Logs-client" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-Kibana Logs-userid" value="allnight87S!@#">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S!@#')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-Kibana Logs-password" value="AD Auth">
                        <button class="copy-btn" onclick="copyToClipboard('AD Auth')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'Kibana Logs')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>IID-Creds</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'IID-Creds')">
                        ⭐
                    </button>
                </div>
                <a href="https://staging.bridger.lexisnexis.eu/xgauth/" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'IID-Creds')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-IID-Creds-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-IID-Creds-userid" value="KrisAj01">
                        <button class="copy-btn" onclick="copyToClipboard('KrisAj01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-IID-Creds-password" value="J9h!8TsA">
                        <button class="copy-btn" onclick="copyToClipboard('J9h!8TsA')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'IID-Creds')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(34, 197, 94);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU Stage Smoke Test - Piplines</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'EU Stage Smoke Test - Piplines')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/eu-stage-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'EU Stage Smoke Test - Piplines')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-EU Stage Smoke Test - Piplines-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-EU Stage Smoke Test - Piplines-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-EU Stage Smoke Test - Piplines-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'EU Stage Smoke Test - Piplines')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : EU - Staging</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'ReadyAPI - PIpline : EU - Staging')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/STAGING-EU.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'ReadyAPI - PIpline : EU - Staging')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-ReadyAPI - PIpline : EU - Staging-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-ReadyAPI - PIpline : EU - Staging-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-ReadyAPI - PIpline : EU - Staging-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'ReadyAPI - PIpline : EU - Staging')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : EU - DR</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuStaging', 'ReadyAPI - PIpline : EU - DR')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/DR-EU.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuStaging', 'ReadyAPI - PIpline : EU - DR')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuStaging-ReadyAPI - PIpline : EU - DR-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuStaging-ReadyAPI - PIpline : EU - DR-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuStaging-ReadyAPI - PIpline : EU - DR-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuStaging', 'ReadyAPI - PIpline : EU - DR')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="EuStaging-name" placeholder="Card name...">
            <input type="url" id="EuStaging-url" placeholder="Card link...">
            <button onclick="addCard('EuStaging')">Add</button>
        </div>
    </div>

    <div class="section" id="EuProd-section">
        <h2>E.U.PROD</h2>
        <div class="container" id="EuProd-container"><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU-AB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU-AB')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.eu" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU-AB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU-AB-client" value="LNSNegereEU ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereEU ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU-AB-userid" value="SNegere16 ">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere16 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU-AB-password" value="Welcome1234~@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234~@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU-AB')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU-prod-Checklist</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU-prod-Checklist')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod.bridger.lexisnexis.eu" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU-prod-Checklist')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU-prod-Checklist-client" value="LNSNegereEU ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereEU ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU-prod-Checklist-userid" value="SNegere16 ">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere16 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU-prod-Checklist-password" value="Welcome1234~@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234~@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU-prod-Checklist')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(147, 51, 234);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU Prod Pipline</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU Prod Pipline')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU Prod Pipline')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU Prod Pipline-client" value="LNSNegereEU ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereEU ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU Prod Pipline-userid" value="EUTester2">
                        <button class="copy-btn" onclick="copyToClipboard('EUTester2')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU Prod Pipline-password" value="Welcome1234~@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234~@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU Prod Pipline')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU Prod Automation</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU Prod Automation')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/eu-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU Prod Automation')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU Prod Automation-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU Prod Automation-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU Prod Automation-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU Prod Automation')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU-Prod- Databridge</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU-Prod- Databridge')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.lexisnexis.eu/" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU-Prod- Databridge')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU-Prod- Databridge-client" value="LNASteve">
                        <button class="copy-btn" onclick="copyToClipboard('LNASteve')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU-Prod- Databridge-userid" value="negeretest1 ">
                        <button class="copy-btn" onclick="copyToClipboard('negeretest1 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU-Prod- Databridge-password" value="Welcome1234~@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234~@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU-Prod- Databridge')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EU PROD Smoke Test - Piplines</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'EU PROD Smoke Test - Piplines')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/eu-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'EU PROD Smoke Test - Piplines')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-EU PROD Smoke Test - Piplines-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-EU PROD Smoke Test - Piplines-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-EU PROD Smoke Test - Piplines-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'EU PROD Smoke Test - Piplines')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline :EU - Prod</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'ReadyAPI - PIpline :EU - Prod')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/PROD-EU.yml" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'ReadyAPI - PIpline :EU - Prod')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-ReadyAPI - PIpline :EU - Prod-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-ReadyAPI - PIpline :EU - Prod-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-ReadyAPI - PIpline :EU - Prod-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'ReadyAPI - PIpline :EU - Prod')">Save</button>
                </div>
            </div><div class="card" data-date="1741888354465" data-category="" style="background-color: rgb(255, 204, 92);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Trace Log</span>
                    <button class="favorite-btn " onclick="toggleFavorite('EuProd', 'Kibana Trace Log')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/s/team-bridger/app/r/s/Kivy7" target="_blank">Visit</a>
                <button onclick="removeCard('EuProd', 'Kibana Trace Log')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="EuProd-Kibana Trace Log-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="EuProd-Kibana Trace Log-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="EuProd-Kibana Trace Log-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('EuProd', 'Kibana Trace Log')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="EuProd-name" placeholder="Card name...">
            <input type="url" id="EuProd-url" placeholder="Card link...">
            <button onclick="addCard('EuProd')">Add</button>
        </div>
    </div>

    <div class="section" id="LoydsLive-section">
        <h2>Lloyds Live</h2>
        <div class="container" id="LoydsLive-container"><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs - "infra_group": "xg5-eu-ldr",</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/s/team-bridger/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:now-120s,to:now))&amp;_a=(columns:!(),filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',key:fields.infra_group,negate:!f,params:(query:xg5-eu-ldr),type:phrase),query:(match_phrase:(fields.infra_group:xg5-eu-ldr)))),index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',interval:auto,query:(language:kuery,query:''),sort:!(!('@timestamp',desc)))" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-client"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-userid"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-password"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs - "infra_group": "xg5-eu-ldr",</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/s/team-bridger/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:now-120s,to:now))&amp;_a=(columns:!(),filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',key:fields.infra_group,negate:!f,params:(query:xg5-eu-ldr),type:phrase),query:(match_phrase:(fields.infra_group:xg5-eu-ldr)))),index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',interval:auto,query:(language:kuery,query:''),sort:!(!('@timestamp',desc)))" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-client"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-userid"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsLive-Kibana Logs - " infra_group":="" "xg5-eu-ldr",-password"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsLive', 'Kibana Logs - " infra_group":="" "xg5-eu-ldr",')"="">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(100, 116, 139);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline :Lloyds - Prod</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Prod')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/PROD-LLOYDS.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Prod')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Prod-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Prod-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Prod-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Prod')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129596" data-category="" style="background-color: rgb(161, 98, 7);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline :Lloyds - Active</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Active')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/PRODACTIVE-LLOYDS.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Active')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Active-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Active-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsLive-ReadyAPI - PIpline :Lloyds - Active-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsLive', 'ReadyAPI - PIpline :Lloyds - Active')">Save</button>
                </div>
            </div><div class="card" data-date="1740423415421" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Lloyds PROD</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsLive', 'Lloyds PROD')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod.lprivatebridger.risk.lexisnexis.eu/XgAuth" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsLive', 'Lloyds PROD')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsLive-Lloyds PROD-client" value="xg5developers">
                        <button class="copy-btn" onclick="copyToClipboard('xg5developers')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsLive-Lloyds PROD-userid" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsLive-Lloyds PROD-password" value="allnight8S@@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsLive', 'Lloyds PROD')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="LoydsLive-name" placeholder="Card name...">
            <input type="url" id="LoydsLive-url" placeholder="Card link...">
            <button onclick="addCard('LoydsLive')">Add</button>
        </div>
    </div>

    <div class="section" id="LoydsDR-section">
        <h2>Lloyds DR</h2>
        <div class="container" id="LoydsDR-container"><div class="card" data-date="1742656129597" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Lloyds DR - Checklist</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'Lloyds DR - Checklist')">
                        ⭐
                    </button>
                </div>
                <a href="https://dr.lprivatebridger.risk.lexisnexis.eu/XgAuth" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'Lloyds DR - Checklist')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-Lloyds DR - Checklist-client" value="xg5developers">
                        <button class="copy-btn" onclick="copyToClipboard('xg5developers')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-Lloyds DR - Checklist-userid" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-Lloyds DR - Checklist-password" value="allnight8S@@@">
                        <button class="copy-btn" onclick="copyToClipboard('allnight8S@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'Lloyds DR - Checklist')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129597" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana - Logs</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'Kibana - Logs')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/s/team-bridger/app/discover#/?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:now-120s,to:now))&amp;_a=(columns:!(),filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',key:fields.infra_group,negate:!f,params:(query:xg5-eu-ldr),type:phrase),query:(match_phrase:(fields.infra_group:xg5-eu-ldr)))),index:'233063b0-8b27-11e9-b2e7-f5a259cf75bc',interval:auto,query:(language:kuery,query:''),sort:!(!('@timestamp',desc)))" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'Kibana - Logs')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-Kibana - Logs-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-Kibana - Logs-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-Kibana - Logs-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'Kibana - Logs')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129597" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>LLOYDS Smoke Test - Piplines</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'LLOYDS Smoke Test - Piplines')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/lloyds-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'LLOYDS Smoke Test - Piplines')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-LLOYDS Smoke Test - Piplines-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-LLOYDS Smoke Test - Piplines-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-LLOYDS Smoke Test - Piplines-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'LLOYDS Smoke Test - Piplines')">Save</button>
                </div>
            </div><div class="card" data-date="1742656129597" data-category="" style="background-color: rgb(100, 116, 139);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI - PIpline : Lloyds - DR</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'ReadyAPI - PIpline : Lloyds - DR')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/DR-LLOYDS.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'ReadyAPI - PIpline : Lloyds - DR')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-ReadyAPI - PIpline : Lloyds - DR-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-ReadyAPI - PIpline : Lloyds - DR-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-ReadyAPI - PIpline : Lloyds - DR-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'ReadyAPI - PIpline : Lloyds - DR')">Save</button>
                </div>
            </div><div class="card" data-date="1740406091283" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>LLOYDS Smoke Test</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'LLOYDS Smoke Test')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/lloyds-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'LLOYDS Smoke Test')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-LLOYDS Smoke Test-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-LLOYDS Smoke Test-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-LLOYDS Smoke Test-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'LLOYDS Smoke Test')">Save</button>
                </div>
            </div><div class="card" data-date="1740406112590" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>API - Lloyds DR</span>
                    <button class="favorite-btn " onclick="toggleFavorite('LoydsDR', 'API - Lloyds DR')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/DR-LLOYDS.yml" target="_blank">Visit</a>
                <button onclick="removeCard('LoydsDR', 'API - Lloyds DR')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="LoydsDR-API - Lloyds DR-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="LoydsDR-API - Lloyds DR-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="LoydsDR-API - Lloyds DR-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('LoydsDR', 'API - Lloyds DR')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="LoydsDR-name" placeholder="Card name...">
            <input type="url" id="LoydsDR-url" placeholder="Card link...">
            <button onclick="addCard('LoydsDR')">Add</button>
        </div>
    </div>

    <div class="section" id="ReadyAPI-section">
        <h2>ReadyAPI Config</h2>
        <div class="container" id="ReadyAPI-container"><div class="card" data-date="1740424899381" data-category="" style="background-color: rgb(150, 206, 180);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Postman Cred</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'Postman Cred')">
                        ⭐
                    </button>
                </div>
                <a href="https://www.postman.com/api-evangelist/plentymarkets/folder/ttpufno/login" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'Postman Cred')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-Postman Cred-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-Postman Cred-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-Postman Cred-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'Postman Cred')">Save</button>
                </div>
            </div><div class="card" data-date="1740424961893" data-category="" style="background-color: rgb(6, 182, 212);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>ReadyAPI Passwords</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'ReadyAPI Passwords')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'ReadyAPI Passwords')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-ReadyAPI Passwords-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-ReadyAPI Passwords-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-ReadyAPI Passwords-password" value="br1dgerAp!">
                        <button class="copy-btn" onclick="copyToClipboard('br1dgerAp!')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'ReadyAPI Passwords')">Save</button>
                </div>
            </div><div class="card" data-date="1741193779355" data-category="" style="background-color: rgb(83, 91, 45);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-NonProd-Client</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'AZ-NonProd-Client')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'AZ-NonProd-Client')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-AZ-NonProd-Client-client" value="postmanClient1">
                        <button class="copy-btn" onclick="copyToClipboard('postmanClient1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-AZ-NonProd-Client-userid" value="postmanTest1">
                        <button class="copy-btn" onclick="copyToClipboard('postmanTest1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-AZ-NonProd-Client-password" value="br1dgerAp!">
                        <button class="copy-btn" onclick="copyToClipboard('br1dgerAp!')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'AZ-NonProd-Client')">Save</button>
                </div>
            </div><div class="card" data-date="1741193982091" data-category="" style="background-color: rgb(250, 204, 21);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-NonProd-Secret</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'AZ-NonProd-Secret')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'AZ-NonProd-Secret')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-AZ-NonProd-Secret-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-AZ-NonProd-Secret-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-AZ-NonProd-Secret-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'AZ-NonProd-Secret')">Save</button>
                </div>
            </div><div class="card" data-date="1741194060983" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-EM</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'AZ-EM')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'AZ-EM')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-AZ-EM-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-AZ-EM-userid" value="syssurafal1">
                        <button class="copy-btn" onclick="copyToClipboard('syssurafal1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-AZ-EM-password" value="abc123$$@">
                        <button class="copy-btn" onclick="copyToClipboard('abc123$$@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'AZ-EM')">Save</button>
                </div>
            </div><div class="card" data-date="1741198118389" data-category="" style="background-color: rgb(154, 212, 206);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Postman setup Token</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'Postman setup Token')">
                        ⭐
                    </button>
                </div>
                <a href="file://risk/inf/QA_Alpha/Bridger%20QA%20Repository/Surafal/API Setup/" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'Postman setup Token')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-Postman setup Token-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-Postman setup Token-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-Postman setup Token-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'Postman setup Token')">Save</button>
                </div>
            </div><div class="card" data-date="1741710318879" data-category="" style="background-color: rgb(212, 165, 165);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>DNS Checker</span>
                    <button class="favorite-btn " onclick="toggleFavorite('ReadyAPI', 'DNS Checker')">
                        ⭐
                    </button>
                </div>
                <a href="https://www.whatsmydns.net/#CNAME/bridger.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('ReadyAPI', 'DNS Checker')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="ReadyAPI-DNS Checker-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="ReadyAPI-DNS Checker-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="ReadyAPI-DNS Checker-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('ReadyAPI', 'DNS Checker')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="ReadyAPI-name" placeholder="Card name...">
            <input type="url" id="ReadyAPI-url" placeholder="Card link...">
            <button onclick="addCard('ReadyAPI')">Add</button>
        </div>
    </div>

    <div class="section" id="Workflows-section">
        <h2>Git Workflows</h2>
        <div class="container" id="Workflows-container"><div class="card" data-date="1740424473899" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>bridger-api-pipeline</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Workflows', 'bridger-api-pipeline')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions" target="_blank">Visit</a>
                <button onclick="removeCard('Workflows', 'bridger-api-pipeline')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Workflows-bridger-api-pipeline-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Workflows-bridger-api-pipeline-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Workflows-bridger-api-pipeline-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Workflows', 'bridger-api-pipeline')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="Workflows-name" placeholder="Card name...">
            <input type="url" id="Workflows-url" placeholder="Card link...">
            <button onclick="addCard('Workflows')">Add</button>
        </div>
    </div>

    <div class="section" id="Automation-section">
        <h2>Automation Testing</h2>
        <div class="container" id="Automation-container"><div class="card" data-date="1741185899630" data-category="" style="background-color: rgb(139, 92, 246);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>bridger-selenium</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Automation', 'bridger-selenium')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium" target="_blank">Visit</a>
                <button onclick="removeCard('Automation', 'bridger-selenium')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Automation-bridger-selenium-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Automation-bridger-selenium-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Automation-bridger-selenium-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Automation', 'bridger-selenium')">Save</button>
                </div>
            </div></div>
        <div class="controls">
            <input type="text" id="Automation-name" placeholder="Card name...">
            <input type="url" id="Automation-url" placeholder="Card link...">
            <button onclick="addCard('Automation')">Add</button>
        </div>
    </div>

    <div id="importStatus" class="import-status"></div>

    <!-- Single notes panel with all functionality -->
    <div id="header-notes" class="notes-panel" style="display: none;">
        <div class="notes-header">
            <h3>Notes</h3>
            <button class="btn" onclick="toggleNotes()">Close</button>
        </div>
        <textarea id="notes-content" placeholder="Add your notes here..."></textarea>
        <div class="notes-controls">
            <button class="btn" onclick="saveNotes()">Save Notes</button>
            <button class="btn" onclick="exportNotes()">Export Notes</button>
            <input type="file" id="import-notes" accept=".txt" onchange="importNotes(event)" style="display: none;">
            <button class="btn" onclick="document.getElementById('import-notes').click()">Import Notes</button>
        </div>
    </div>
    </div>

    <script>
        // Store cards data
        let cardsData = {};

        // Initialize the application
        function initializeApp() {
            // Load saved cards from localStorage
            const savedData = localStorage.getItem('cardsData');
            if (savedData) {
                cardsData = JSON.parse(savedData);
            }

            // Load sections and their cards
            loadSections();

            // Render all cards
            renderAllCards();
        }

        // Render all cards from stored data
        function renderAllCards() {
            Object.keys(cardsData).forEach(section => {
                const container = document.getElementById(`${section}-container`);
                if (container) {
                    container.innerHTML = '';
                    cardsData[section].forEach(card => {
                        createCard(section, card.name, card.url, card.color);
                    });
                }
            });
        }

        function createCard(section, name, url, color = getRandomColor()) {
            const container = document.getElementById(`${section}-container`);
            if (!container) return;

            const cardData = cardsData[section]?.find(card => card.name === name);
            const clientInfo = cardData?.clientInfo || { clientName: '', userId: '', password: '' };
            const isFavorite = cardData?.favorite || false;

            const card = document.createElement('div');
            card.className = 'card';
            card.style.backgroundColor = color;
            card.dataset.date = cardData?.createdAt || Date.now();
            card.dataset.category = cardData?.category || '';

            card.innerHTML = `
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>${name}</span>
                    <button class="favorite-btn ${isFavorite ? 'active' : ''}" onclick="toggleFavorite('${section}', '${name}')">
                        ⭐
                    </button>
                </div>
                ${url ? `<a href="${url}" target="_blank">Visit</a>` : ''}
                <button onclick="removeCard('${section}', '${name}')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="${section}-${name}-client" value="${clientInfo.clientName || ''}">
                        <button class="copy-btn" onclick="copyToClipboard('${clientInfo.clientName}')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="${section}-${name}-userid" value="${clientInfo.userId || ''}">
                        <button class="copy-btn" onclick="copyToClipboard('${clientInfo.userId}')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="${section}-${name}-password" value="${clientInfo.password || ''}">
                        <button class="copy-btn" onclick="copyToClipboard('${clientInfo.password}')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('${section}', '${name}')">Save</button>
                </div>
            `;

            container.appendChild(card);
        }

        // Add a new card
        function addCard(section) {
            const nameInput = document.getElementById(`${section}-name`);
            const urlInput = document.getElementById(`${section}-url`);
            const name = nameInput.value.trim();
            const url = urlInput.value.trim();

            if (!name) {
                alert('Please enter a card name');
                return;
            }

            if (url && !isValidUrl(url)) {
                alert('Please enter a valid URL');
                return;
            }

            // Initialize section in cardsData if it doesn't exist
            if (!cardsData[section]) {
                cardsData[section] = [];
            }

            // Create a new card object
            const newCard = {
                name,
                url,
                color: getRandomColor(),
                clientInfo: {
                    clientName: '',
                    userId: '',
                    password: ''
                },
                favorite: false,
                createdAt: Date.now(),
                category: ''
            };

            // Add the card to the cardsData object
            cardsData[section].push(newCard);

            // Save both the cardsData and the card to localStorage
            saveToLocalStorage();
            localStorage.setItem(section, JSON.stringify(cardsData[section]));

            // Create the visual card
            createCard(section, name, url, newCard.color);

            // Clear inputs
            nameInput.value = '';
            urlInput.value = '';
        }

        // Remove a card
        function removeCard(section, name) {
            if (confirm('Are you sure you want to remove this card?')) {
                cardsData[section] = cardsData[section].filter(card => card.name !== name);
                saveToLocalStorage();
                renderAllCards();
            }
        }

        // Save card information
        function saveCardInfo(section, name) {
            const clientInput = document.getElementById(`${section}-${name}-client`);
            const userIdInput = document.getElementById(`${section}-${name}-userid`);
            const passwordInput = document.getElementById(`${section}-${name}-password`);

            const cardIndex = cardsData[section].findIndex(card => card.name === name);
            if (cardIndex !== -1) {
                cardsData[section][cardIndex].clientInfo = {
                    clientName: clientInput.value,
                    userId: userIdInput.value,
                    password: passwordInput.value
                };
                saveToLocalStorage();
                alert('Card information saved successfully!');
            }
        }

        // Helper functions
        function getRandomColor() {
            const colors = [
            // Original colors
            '#22c55e', // green
            '#2563eb', // blue
            '#facc15', // yellow
            '#f97316', // orange
            '#9333ea', // purple
            '#db2777', // pink
            
            // First set of additions
            '#ef4444', // red
            '#06b6d4', // cyan
            '#14b8a6', // teal
            '#8b5cf6', // violet
            '#64748b', // slate
            '#a16207', // amber
            '#15803d', // emerald
            '#7c2d12', // warm brown
            '#831843', // deep pink
            
            // Additional new colors
            '#2d335b', // navy blue
            '#535b2d', // olive
            '#494949', // charcoal
            '#d7d7d7', // light gray
            '#9ad4ce', // seafoam
            '#ff6b6b', // coral
            '#4ecdc4', // turquoise
            '#45b7d1', // sky blue
            '#96ceb4', // sage
            '#ff6f69', // salmon
            '#588c7e', // forest green
            '#ffcc5c', // golden yellow
            '#96ceb4', // mint
            '#d4a5a5', // dusty rose
            '#392f5a'  // deep purple
        ];
            return colors[Math.floor(Math.random() * colors.length)];
        }

        function isValidUrl(string) {
            try {
                new URL(string);
                return true;
            } catch (_) {
                return false;
            }
        }

        // Export function
        function exportData() {
            try {
                // Get all cards data from localStorage
                const exportData = [];
                const sections = ["general", "development", "design,U.S. Staging - Green ", "U.S. Staging - Blue","META MPC", "Block MPC", "usPROD", "E.U.Staging","E.U.PROD", "LoydsLive", "Lloyds DR", "Git Workflows", "ReadyAPI Config","Automation Testing"]; // Add all your sections here

                sections.forEach(section => {
                    const container = document.getElementById(`${section}-container`);
                    if (!container) return;

                    // Get all cards in this section
                    const cards = container.getElementsByClassName('card');
                    Array.from(cards).forEach(card => {
                        const name = card.querySelector('span').textContent;
                        const url = card.querySelector('a')?.href || '';
                        const color = card.style.backgroundColor;
                        
                        // Get the card's stored information
                        const cardData = cardsData[section]?.find(c => c.name === name) || {};
                        
                        exportData.push({
                            section: section,
                            name: name,
                            url: url,
                            color: color,
                            clientInfo: cardData.clientInfo || {
                                clientName: '',
                                userId: '',
                                password: ''
                            }
                        });
                    });
                });

                // Create and download JSON file
                const blob = new Blob([JSON.stringify(exportData, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const link = document.createElement('a');
                link.href = url;
                link.download = `qa-environments-${new Date().toISOString().slice(0,10)}.json`;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
                URL.revokeObjectURL(url);

                showStatus('Data exported successfully!');
            } catch (error) {
                console.error('Export error:', error);
                showStatus('Export failed: ' + error.message, true);
            }
        }

        function importData(event) {
            const file = event.target.files[0];
            if (!file) {
                showStatus('No file selected', true);
                return;
            }

            const reader = new FileReader();
            
            reader.onload = function(e) {
                try {
                    const importedData = JSON.parse(e.target.result);
                    
                    // Clear existing cards
                    cardsData = {};
                    
                    // Initialize sections with correct IDs
                    const sections = [
                        "general", 
                        "development", 
                        "design", 
                        "Green", 
                        "Blue", 
                        "META",
                        "Block",
                        "usPROD", 
                        "EuStaging",
                        "EuProd", 
                        "LoydsLive", 
                        "LoydsDR",
                        "Workflows",
                        "ReadyAPI", 
                        "Automation"
                    ];

                    sections.forEach(section => {
                        const container = document.getElementById(`${section}-container`);
                        if (container) {
                            container.innerHTML = '';
                        }
                        cardsData[section] = [];
                    });

                    // Import new cards
                    importedData.forEach(item => {
                        if (!cardsData[item.section]) {
                            cardsData[item.section] = [];
                        }

                        // Add card to cardsData
                        cardsData[item.section].push({
                            name: item.name,
                            url: item.url,
                            color: item.color,
                            clientInfo: item.clientInfo || {
                                clientName: '',
                                userId: '',
                                password: ''
                            }
                        });

                        // Create visual card
                        createCard(item.section, item.name, item.url, item.color);
                    });

                    // Save to localStorage
                    saveToLocalStorage();
                    
                    showStatus('Data imported successfully!');
                } catch (error) {
                    console.error('Import error:', error);
                    showStatus('Import failed: ' + error.message, true);
                }
            };

            reader.onerror = function() {
                showStatus('Error reading file', true);
            };

            reader.readAsText(file);
        }

        // Status message helper function
        function showStatus(message, isError = false) {
            const statusElement = document.getElementById('importStatus');
            if (!statusElement) {
                console.error('Status element not found');
                return;
            }
            
            statusElement.textContent = message;
            statusElement.className = `import-status ${isError ? 'error' : 'success'}`;
            statusElement.style.display = 'block';
            
            setTimeout(() => {
                statusElement.style.display = 'none';
            }, 3000);
        }

        // Initialize notes variable
        let headerNotes = localStorage.getItem('headerNotes') || '';

        // Toggle notes panel visibility
        function toggleNotes() {
            const notesPanel = document.getElementById('header-notes');
            if (!notesPanel) return;
            
            const isHidden = notesPanel.style.display === 'none';
            notesPanel.style.display = isHidden ? 'block' : 'none';
            
            if (isHidden) {
                // Load saved notes when showing panel
                const notesContent = document.getElementById('notes-content');
                if (notesContent) {
                    notesContent.value = headerNotes;
                }
            }
        }

        // Save notes
        function saveNotes() {
            const notesContent = document.getElementById('notes-content');
            if (!notesContent) return;
            
            headerNotes = notesContent.value;
            localStorage.setItem('headerNotes', headerNotes);
            showStatus('Notes saved successfully!');
        }

        // Export notes
        function exportNotes() {
            const notes = headerNotes;
            const blob = new Blob([notes], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `qa-environment-notes-${new Date().toISOString().slice(0,10)}.txt`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
            showStatus('Notes exported successfully!');
        }

        // Import notes
        function importNotes(event) {
            const file = event.target.files[0];
            if (!file) {
                showStatus('No file selected', true);
                return;
            }

            const reader = new FileReader();
            
            reader.onload = function(e) {
                try {
                    const importedNotes = e.target.result;
                    headerNotes = importedNotes;
                    
                    const notesContent = document.getElementById('notes-content');
                    if (notesContent) {
                        notesContent.value = headerNotes;
                    }
                    
                    localStorage.setItem('headerNotes', headerNotes);
                    showStatus('Notes imported successfully!');
                } catch (error) {
                    console.error('Notes import error:', error);
                    showStatus('Notes import failed: ' + error.message, true);
                }
            };

            reader.onerror = function() {
                showStatus('Error reading notes file', true);
            };

            reader.readAsText(file);
        }

        function saveToLocalStorage() {
            // Save main cardsData
            localStorage.setItem('cardsData', JSON.stringify(cardsData));
            
            // Save individual section data
            Object.keys(cardsData).forEach(section => {
                localStorage.setItem(section, JSON.stringify(cardsData[section]));
            });
        }

        // Initialize the app when the page loads
        window.onload = function() {
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme) {
                document.body.setAttribute('data-theme', savedTheme);
            }
            initializeApp();
        };
        
        function toggleDarkMode() {
            const body = document.body;
            const isDarkMode = body.getAttribute('data-theme') === 'dark';
            body.setAttribute('data-theme', isDarkMode ? 'light' : 'dark');
            localStorage.setItem('theme', isDarkMode ? 'light' : 'dark');
        }

        // Function to load sections and their cards from localStorage
        function loadSections() {
            const savedSections = JSON.parse(localStorage.getItem('sections')) || [];
            savedSections.forEach(sectionName => {
                // Initialize section in cardsData
                if (!cardsData[sectionName]) {
                    cardsData[sectionName] = [];
                }

                // Create section HTML
                const newSectionHTML = `
                    <div class="section" id="${sectionName}-section">
                        <div class="section-header">
                            <h2>${sectionName}</h2>
                            <button class="delete-section-btn" onclick="deleteSection('${sectionName}')">Delete Section</button>
                        </div>
                        <div class="container" id="${sectionName}-container"></div>
                        <div class="controls">
                            <input type="text" id="${sectionName}-name" placeholder="Card name...">
                            <input type="url" id="${sectionName}-url" placeholder="Card link...">
                            <button onclick="addCard('${sectionName}')">Add</button>
                        </div>
                    </div>
                `;
                document.body.appendChild(createElementFromHTML(newSectionHTML));

                // Load cards for this section
                const sectionCards = JSON.parse(localStorage.getItem(sectionName)) || [];
                cardsData[sectionName] = sectionCards; // Update cardsData with saved cards
                sectionCards.forEach(card => {
                    createCard(sectionName, card.name, card.url, card.color);
                });
            });
        }

        // Function to add a new section
        function addNewSection() {
            const sectionNameInput = document.getElementById('new-section-name');
            const sectionName = sectionNameInput.value.trim();

            if (!sectionName) {
                alert('Please enter a section name');
                return;
            }

            // Create a new section in the cardsData object
            if (!cardsData[sectionName]) {
                cardsData[sectionName] = [];
            }

            // Save the new section to localStorage
            const savedSections = JSON.parse(localStorage.getItem('sections')) || [];
            if (!savedSections.includes(sectionName)) {
                savedSections.push(sectionName);
                localStorage.setItem('sections', JSON.stringify(savedSections));
            }

            // Create a new section in the HTML
            const newSectionHTML = `
                <div class="section" id="${sectionName}-section">
                    <div class="section-header">
                        <h2>${sectionName}</h2>
                        <button class="delete-section-btn" onclick="deleteSection('${sectionName}')">Delete Section</button>
                    </div>
                    <div class="container" id="${sectionName}-container"></div>
                    <div class="controls">
                        <input type="text" id="${sectionName}-name" placeholder="Card name...">
                        <input type="url" id="${sectionName}-url" placeholder="Card link...">
                        <button onclick="addCard('${sectionName}')">Add</button>
                    </div>
                </div>
            `;

            // Append the new section to the body or a specific container
            document.body.appendChild(createElementFromHTML(newSectionHTML));

            // Clear the input field
            sectionNameInput.value = '';
        }

        // Function to delete a section
        function deleteSection(sectionName) {
            if (confirm(`Are you sure you want to delete the "${sectionName}" section and all its cards?`)) {
                // Remove from localStorage
                const savedSections = JSON.parse(localStorage.getItem('sections')) || [];
                const updatedSections = savedSections.filter(section => section !== sectionName);
                localStorage.setItem('sections', JSON.stringify(updatedSections));
                
                // Remove section's cards from localStorage
                localStorage.removeItem(sectionName);
                
                // Remove from cardsData
                delete cardsData[sectionName];
                
                // Remove from DOM
                const sectionElement = document.getElementById(`${sectionName}-section`);
                if (sectionElement) {
                    sectionElement.remove();
                }
                
                showStatus('Section deleted successfully!');
            }
        }

        // Helper function to create an element from HTML string
        function createElementFromHTML(htmlString) {
            const div = document.createElement('div');
            div.innerHTML = htmlString.trim();
            return div.firstChild;
        }

        // Search/Filter functionality
        function filterCards(searchTerm) {
            const cards = document.querySelectorAll('.card');
            searchTerm = searchTerm.toLowerCase();
            
            cards.forEach(card => {
                const cardText = card.textContent.toLowerCase();
                card.style.display = cardText.includes(searchTerm) ? '' : 'none';
            });
        }

        // Sort functionality
        function sortCards(criteria) {
            Object.keys(cardsData).forEach(section => {
                const container = document.getElementById(`${section}-container`);
                if (!container) return;

                const cards = Array.from(container.children);
                cards.sort((a, b) => {
                    switch(criteria) {
                        case 'name':
                            return a.querySelector('span').textContent.localeCompare(b.querySelector('span').textContent);
                        case 'date':
                            return (b.dataset.date || 0) - (a.dataset.date || 0);
                        case 'category':
                            return (a.dataset.category || '').localeCompare(b.dataset.category || '');
                        default:
                            return 0;
                    }
                });

                cards.forEach(card => container.appendChild(card));
            });
        }

        // Quick copy functionality
        function copyToClipboard(text) {
            navigator.clipboard.writeText(text).then(() => {
                showStatus('Copied to clipboard!');
            }).catch(err => {
                console.error('Failed to copy:', err);
            });
        }

        // Toggle favorite functionality
        function toggleFavorite(section, name) {
            const cardIndex = cardsData[section].findIndex(card => card.name === name);
            if (cardIndex !== -1) {
                cardsData[section][cardIndex].favorite = !cardsData[section][cardIndex].favorite;
                saveToLocalStorage();
                renderAllCards();
            }
        }

        // Function to generate a random client name from a dictionary
        function generateRandomClient() {
            const clients = [
                'Acme Corp', 'Globex Corporation', 'Initech', 'Umbrella Corp', 
                'Hooli', 'Stark Industries', 'Wayne Enterprises', 'Dunder Mifflin', 
                'Buy N Large', 'Massive Dynamic'
            ];
            const randomClient = clients[Math.floor(Math.random() * clients.length)];
            document.getElementById('random-client').value = randomClient;
        }

        // Function to generate a random username from a dictionary
        function generateRandomUsername() {
            const usernames = [
                'user123', 'guest456', 'admin789', 'testUser', 
                'randomUser', 'johnDoe', 'janeDoe', 'superUser', 
                'coolCat', 'mightyMouse'
            ];
            const randomUsername = usernames[Math.floor(Math.random() * usernames.length)];
            document.getElementById('random-username').value = randomUsername;
        }

        // Function to generate a random password
        function generateRandomPassword() {
            const length = 12;
            const charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+";
            let password = "";
            for (let i = 0; i < length; i++) {
                password += charset.charAt(Math.floor(Math.random() * charset.length));
            }
            document.getElementById('random-password').value = password;
        }
    </script>


<div class="section" id="SSMS/MYSQL - DB Config-section">
                        <div class="section-header">
                            <h2>SSMS/MYSQL - DB Config</h2>
                            <button class="delete-section-btn" onclick="deleteSection('SSMS/MYSQL - DB Config')">Delete Section</button>
                        </div>
                        <div class="container" id="SSMS/MYSQL - DB Config-container"><div class="card" data-date="1740425111859" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>QA301 DB</span>
                    <button class="favorite-btn " onclick="toggleFavorite('SSMS/MYSQL - DB Config', 'QA301 DB')">
                        ⭐
                    </button>
                </div>
                <a href="https://www.mysql.com/" target="_blank">Visit</a>
                <button onclick="removeCard('SSMS/MYSQL - DB Config', 'QA301 DB')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="SSMS/MYSQL - DB Config-QA301 DB-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="SSMS/MYSQL - DB Config-QA301 DB-userid" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="SSMS/MYSQL - DB Config-QA301 DB-password" value="allnight87S@!~!">
                        <button class="copy-btn" onclick="copyToClipboard('allnight87S@!~!')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('SSMS/MYSQL - DB Config', 'QA301 DB')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="SSMS/MYSQL - DB Config-name" placeholder="Card name...">
                            <input type="url" id="SSMS/MYSQL - DB Config-url" placeholder="Card link...">
                            <button onclick="addCard('SSMS/MYSQL - DB Config')">Add</button>
                        </div>
                    </div><div class="section" id="Enterprise Bundle - Test-section">
                        <div class="section-header">
                            <h2>Enterprise Bundle - Test</h2>
                            <button class="delete-section-btn" onclick="deleteSection('Enterprise Bundle - Test')">Delete Section</button>
                        </div>
                        <div class="container" id="Enterprise Bundle - Test-container"><div class="card" data-date="1740498721599" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Server 401</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'Server 401')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawqbrg401.risk.regn.net/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('Enterprise Bundle - Test', 'Server 401')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-Server 401-client" value="clientauth">
                        <button class="copy-btn" onclick="copyToClipboard('clientauth')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-Server 401-userid" value="risk">
                        <button class="copy-btn" onclick="copyToClipboard('risk')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-Server 401-password" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'Server 401')">Save</button>
                </div>
            </div><div class="card" data-date="1740498852381" data-category="" style="background-color: rgb(100, 116, 139);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Server - 405</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'Server - 405')">
                        ⭐
                    </button>
                </div>
                <a href="https://alawqbrg405.risk.regn.net/XgAuth" target="_blank">Visit</a>
                <button onclick="removeCard('Enterprise Bundle - Test', 'Server - 405')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-Server - 405-client" value="clientauth">
                        <button class="copy-btn" onclick="copyToClipboard('clientauth')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-Server - 405-userid" value="risk">
                        <button class="copy-btn" onclick="copyToClipboard('risk')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-Server - 405-password" value="negesu01">
                        <button class="copy-btn" onclick="copyToClipboard('negesu01')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'Server - 405')">Save</button>
                </div>
            </div><div class="card" data-date="1740687148013" data-category="" style="background-color: rgb(215, 215, 215);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Default -CRED</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'Default -CRED')">
                        ⭐
                    </button>
                </div>
                
                <button onclick="removeCard('Enterprise Bundle - Test', 'Default -CRED')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-Default -CRED-client" value="sysuser1">
                        <button class="copy-btn" onclick="copyToClipboard('sysuser1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-Default -CRED-userid" value="password1!">
                        <button class="copy-btn" onclick="copyToClipboard('password1!')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-Default -CRED-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'Default -CRED')">Save</button>
                </div>
            </div><div class="card" data-date="1740689537012" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>EM Clinet</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'EM Clinet')">
                        ⭐
                    </button>
                </div>
                
                <button onclick="removeCard('Enterprise Bundle - Test', 'EM Clinet')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-EM Clinet-client" value="EClient1">
                        <button class="copy-btn" onclick="copyToClipboard('EClient1')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-EM Clinet-userid" value="Admin123">
                        <button class="copy-btn" onclick="copyToClipboard('Admin123')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-EM Clinet-password" value="password1!">
                        <button class="copy-btn" onclick="copyToClipboard('password1!')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'EM Clinet')">Save</button>
                </div>
            </div><div class="card" data-date="1740746404019" data-category="" style="background-color: rgb(219, 39, 119);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Enterprise Environments and Setup</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'Enterprise Environments and Setup')">
                        ⭐
                    </button>
                </div>
                <a href="https://confluence.rsi.lexisnexis.com/display/BTU/Enterprise+Environments+and+Setup" target="_blank">Visit</a>
                <button onclick="removeCard('Enterprise Bundle - Test', 'Enterprise Environments and Setup')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-Enterprise Environments and Setup-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-Enterprise Environments and Setup-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-Enterprise Environments and Setup-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'Enterprise Environments and Setup')">Save</button>
                </div>
            </div><div class="card" data-date="1742425313410" data-category="" style="background-color: rgb(69, 183, 209);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Confluence Page</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Enterprise Bundle - Test', 'Confluence Page')">
                        ⭐
                    </button>
                </div>
                <a href="https://statics.teams.cdn.office.net/evergreen-assets/safelinks/1/atp-safelinks.html" target="_blank">Visit</a>
                <button onclick="removeCard('Enterprise Bundle - Test', 'Confluence Page')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Enterprise Bundle - Test-Confluence Page-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Enterprise Bundle - Test-Confluence Page-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Enterprise Bundle - Test-Confluence Page-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Enterprise Bundle - Test', 'Confluence Page')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="Enterprise Bundle - Test-name" placeholder="Card name...">
                            <input type="url" id="Enterprise Bundle - Test-url" placeholder="Card link...">
                            <button onclick="addCard('Enterprise Bundle - Test')">Add</button>
                        </div>
                    </div><div class="section" id="US-PROD-BLUE-section">
                        <div class="section-header">
                            <h2>US-PROD-BLUE</h2>
                            <button class="delete-section-btn" onclick="deleteSection('US-PROD-BLUE')">Delete Section</button>
                        </div>
                        <div class="container" id="US-PROD-BLUE-container"><div class="card" data-date="1740506476939" data-category="" style="background-color: rgb(45, 51, 91);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>API - Blue (Run Workflow)</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'API - Blue (Run Workflow)')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/AZURE-PROD%20BLUE.yml" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'API - Blue (Run Workflow)')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-API - Blue (Run Workflow)-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-API - Blue (Run Workflow)-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-API - Blue (Run Workflow)-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'API - Blue (Run Workflow)')">Save</button>
                </div>
            </div><div class="card" data-date="1740506507230" data-category="" style="background-color: rgb(100, 116, 139);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Smoke Test(Update Version)</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'Smoke Test(Update Version)')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/us-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'Smoke Test(Update Version)')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-Smoke Test(Update Version)-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-Smoke Test(Update Version)-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-Smoke Test(Update Version)-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'Smoke Test(Update Version)')">Save</button>
                </div>
            </div><div class="card" data-date="1740506528000" data-category="" style="background-color: rgb(212, 165, 165);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Checklist - inactive site</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'Checklist - inactive site')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod0.bridger.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'Checklist - inactive site')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-Checklist - inactive site-client" value="LNSNegereUS ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUS ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-Checklist - inactive site-userid" value="SNegere33 ">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere33 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-Checklist - inactive site-password" value="Welcome1234!!@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234!!@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'Checklist - inactive site')">Save</button>
                </div>
            </div><div class="card" data-date="1740506651353" data-category="" style="background-color: rgb(45, 51, 91);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>SFTP-IN</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'SFTP-IN')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod0.bridger.lexisnexisrisk.com/XgApp/Batch/BatchRuns" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'SFTP-IN')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-SFTP-IN-client" value="BridgerFTP.lexisnexisrisk.com">
                        <button class="copy-btn" onclick="copyToClipboard('BridgerFTP.lexisnexisrisk.com')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-SFTP-IN-userid" value="LNSNegereUS">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUS')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-SFTP-IN-password" value="yHd9*b}C=ro=K">
                        <button class="copy-btn" onclick="copyToClipboard('yHd9*b}C=ro=K')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'SFTP-IN')">Save</button>
                </div>
            </div><div class="card" data-date="1740506702120" data-category="" style="background-color: rgb(21, 128, 61);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>SFTP - OUT</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'SFTP - OUT')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod0.bridger.lexisnexisrisk.com/XgApp/Batch/BatchRuns" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'SFTP - OUT')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-SFTP - OUT-client" value="BridgerFTP.lexisnexisrisk.com">
                        <button class="copy-btn" onclick="copyToClipboard('BridgerFTP.lexisnexisrisk.com')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-SFTP - OUT-userid" value="LNSNegereUSOut">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUSOut')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-SFTP - OUT-password" value="HFhyct^*B2WB*">
                        <button class="copy-btn" onclick="copyToClipboard('HFhyct^*B2WB*')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'SFTP - OUT')">Save</button>
                </div>
            </div><div class="card" data-date="1740509279141" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>FraudPoint® Score Cred</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'FraudPoint® Score Cred')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod0.bridger.lexisnexisrisk.com/XgApp/SystemAccess/Providers" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'FraudPoint® Score Cred')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-FraudPoint® Score Cred-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-FraudPoint® Score Cred-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-FraudPoint® Score Cred-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'FraudPoint® Score Cred')">Save</button>
                </div>
            </div><div class="card" data-date="1740509293084" data-category="" style="background-color: rgb(78, 205, 196);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>InstantID® - Cred</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'InstantID® - Cred')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod0.bridger.lexisnexisrisk.com/XgApp/SystemAccess/Providers" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'InstantID® - Cred')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-InstantID® - Cred-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-InstantID® - Cred-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-InstantID® - Cred-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'InstantID® - Cred')">Save</button>
                </div>
            </div><div class="card" data-date="1740510341568" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AML- Creds</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'AML- Creds')">
                        ⭐
                    </button>
                </div>
                <a href="https://amlinsight.lexisnexisrisk.com/app/bps/main?version=1&amp;timestamp=2025-02-25T19%3A03%3A43.2187852Z&amp;goto=form&amp;xgsourceid=50d81d9bd6c8414e9ac622efac2a7cd4&amp;xgcustomerid=47173&amp;xguserid=2763723&amp;xgrecordid=19877733349&amp;target=PERSON_SEARCH&amp;query=%3CfieldList%3E%3Cfield%20name%3D%22LastName%22%3Eladen%3C%2Ffield%3E%3Cfield%20name%3D%22FirstName%22%3Eosama%3C%2Ffield%3E%3Cfield%20name%3D%22MiddleName%22%3E%20%3C%2Ffield%3E%3Cfield%20name%3D%22Address1%22%3E%20%3C%2Ffield%3E%3Cfield%20name%3D%22City%22%3E%20%3C%2Ffield%3E%3Cfield%20name%3D%22State%22%3E%20%3C%2Ffield%3E%3Cfield%20name%3D%22Zip5%22%3E%20%3C%2Ffield%3E%3Cfield%20name%3D%22Phone%22%3E%20%3C%2Ffield%3E%3C%2FfieldList%3E&amp;checksum=B2lrtBBvDotAoVOD7KAkGg2" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'AML- Creds')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-AML- Creds-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-AML- Creds-userid" value="krisaj01_cp">
                        <button class="copy-btn" onclick="copyToClipboard('krisaj01_cp')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-AML- Creds-password" value="Lexis@1996">
                        <button class="copy-btn" onclick="copyToClipboard('Lexis@1996')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'AML- Creds')">Save</button>
                </div>
            </div><div class="card" data-date="1740520969220" data-category="" style="background-color: rgb(69, 183, 209);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>AZ-US Prod</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'AZ-US Prod')">
                        ⭐
                    </button>
                </div>
                <a href="https://elk.us-logs-prod.azure.lnrsg.io/" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'AZ-US Prod')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-AZ-US Prod-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-AZ-US Prod-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-AZ-US Prod-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'AZ-US Prod')">Save</button>
                </div>
            </div><div class="card" data-date="1740522933151" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Kibana Logs - Xg5-us-dr</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'Kibana Logs - Xg5-us-dr')">
                        ⭐
                    </button>
                </div>
                <a href="https://bselk.risk.regn.net/s/team-bridger/app/r/s/44lO7" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'Kibana Logs - Xg5-us-dr')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-Kibana Logs - Xg5-us-dr-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-Kibana Logs - Xg5-us-dr-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-Kibana Logs - Xg5-us-dr-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'Kibana Logs - Xg5-us-dr')">Save</button>
                </div>
            </div><div class="card" data-date="1740753522598" data-category="" style="background-color: rgb(88, 140, 126);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Jira - Guidance</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-BLUE', 'Jira - Guidance')">
                        ⭐
                    </button>
                </div>
                <a href="https://jira.rsi.lexisnexis.com/browse/XG5-82285" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-BLUE', 'Jira - Guidance')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-BLUE-Jira - Guidance-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-BLUE-Jira - Guidance-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-BLUE-Jira - Guidance-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-BLUE', 'Jira - Guidance')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="US-PROD-BLUE-name" placeholder="Card name...">
                            <input type="url" id="US-PROD-BLUE-url" placeholder="Card link...">
                            <button onclick="addCard('US-PROD-BLUE')">Add</button>
                        </div>
                    </div><div class="section" id="Kubernetes cluster-section">
                        <div class="section-header">
                            <h2>Kubernetes cluster</h2>
                            <button class="delete-section-btn" onclick="deleteSection('Kubernetes cluster')">Delete Section</button>
                        </div>
                        <div class="container" id="Kubernetes cluster-container"><div class="card" data-date="1741101042360" data-category="" style="background-color: rgb(69, 183, 209);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>How To: Setup Access to Kubernetes cluster</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Kubernetes cluster', 'How To: Setup Access to Kubernetes cluster')">
                        ⭐
                    </button>
                </div>
                <a href="https://confluence.rsi.lexisnexis.com/display/BTU/How+To%3A+Setup+Access+to+Kubernetes+cluster" target="_blank">Visit</a>
                <button onclick="removeCard('Kubernetes cluster', 'How To: Setup Access to Kubernetes cluster')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Kubernetes cluster-How To: Setup Access to Kubernetes cluster-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Kubernetes cluster-How To: Setup Access to Kubernetes cluster-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Kubernetes cluster-How To: Setup Access to Kubernetes cluster-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Kubernetes cluster', 'How To: Setup Access to Kubernetes cluster')">Save</button>
                </div>
            </div><div class="card" data-date="1741696742235" data-category="" style="background-color: rgb(73, 73, 73);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-dev.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-dev --resource-group app-bridger-dev-eastus --name app-bridger-dev-eastus-aks-1')">Save</button>
                </div>
            </div><div class="card" data-date="1741696777329" data-category="" style="background-color: rgb(154, 212, 206);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1</span>
                    <button class="favorite-btn " onclick="toggleFavorite('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1')">
                        ⭐
                    </button>
                </div>
                <a href="https://bridger.us-bridger-nonprod.azure.lnrsg.io/XgAuth/" target="_blank">Visit</a>
                <button onclick="removeCard('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="Kubernetes cluster-az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('Kubernetes cluster', 'az aks get-credentials --subscription us-bridger-nonprod --resource-group app-bridger-nonprod-eastus --name app-bridger-nonprod-eastus-aks-1')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="Kubernetes cluster-name" placeholder="Card name...">
                            <input type="url" id="Kubernetes cluster-url" placeholder="Card link...">
                            <button onclick="addCard('Kubernetes cluster')">Add</button>
                        </div>
                    </div><div class="section" id="5.83 - AZ-NonProd Task-section">
                        <div class="section-header">
                            <h2>5.83 - AZ-NonProd Task</h2>
                            <button class="delete-section-btn" onclick="deleteSection('5.83 - AZ-NonProd Task')">Delete Section</button>
                        </div>
                        <div class="container" id="5.83 - AZ-NonProd Task-container"><div class="card" data-date="1741192059192" data-category="" style="background-color: rgb(37, 99, 235);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Run Regression Test in Azure Non Prod environment for 5.83 Release</span>
                    <button class="favorite-btn " onclick="toggleFavorite('5.83 - AZ-NonProd Task', 'Run Regression Test in Azure Non Prod environment for 5.83 Release')">
                        ⭐
                    </button>
                </div>
                <a href="https://jira.rsi.lexisnexis.com/browse/XG5-81635" target="_blank">Visit</a>
                <button onclick="removeCard('5.83 - AZ-NonProd Task', 'Run Regression Test in Azure Non Prod environment for 5.83 Release')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="5.83 - AZ-NonProd Task-Run Regression Test in Azure Non Prod environment for 5.83 Release-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="5.83 - AZ-NonProd Task-Run Regression Test in Azure Non Prod environment for 5.83 Release-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="5.83 - AZ-NonProd Task-Run Regression Test in Azure Non Prod environment for 5.83 Release-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('5.83 - AZ-NonProd Task', 'Run Regression Test in Azure Non Prod environment for 5.83 Release')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="5.83 - AZ-NonProd Task-name" placeholder="Card name...">
                            <input type="url" id="5.83 - AZ-NonProd Task-url" placeholder="Card link...">
                            <button onclick="addCard('5.83 - AZ-NonProd Task')">Add</button>
                        </div>
                    </div><div class="section" id="QA-Copilot-section">
                        <div class="section-header">
                            <h2>QA-Copilot</h2>
                            <button class="delete-section-btn" onclick="deleteSection('QA-Copilot')">Delete Section</button>
                        </div>
                        <div class="container" id="QA-Copilot-container"><div class="card" data-date="1741283825533" data-category="" style="background-color: rgb(100, 116, 139);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>VS code Extension "QA-Copilot"</span>
                    <button class="favorite-btn " onclick="toggleFavorite('QA-Copilot', 'VS code Extension " qa-copilot"')"="">
                        ⭐
                    </button>
                </div>
                <a href="https://confluence.rsi.lexisnexis.com/pages/viewpage.action?pageId=528258202" target="_blank">Visit</a>
                <button onclick="removeCard('QA-Copilot', 'VS code Extension " qa-copilot"')"="">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="QA-Copilot-VS code Extension " qa-copilot"-client"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="QA-Copilot-VS code Extension " qa-copilot"-userid"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="QA-Copilot-VS code Extension " qa-copilot"-password"="" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('QA-Copilot', 'VS code Extension " qa-copilot"')"="">Save</button>
                </div>
            </div><div class="card" data-date="1741283879371" data-category="" style="background-color: rgb(154, 212, 206);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Group Community</span>
                    <button class="favorite-btn " onclick="toggleFavorite('QA-Copilot', 'Group Community')">
                        ⭐
                    </button>
                </div>
                <a href="https://engage.cloud.microsoft/main/org/relx.com/groups/eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIyMjAyMzU5Mzk4NDAifQ/all" target="_blank">Visit</a>
                <button onclick="removeCard('QA-Copilot', 'Group Community')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="QA-Copilot-Group Community-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="QA-Copilot-Group Community-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="QA-Copilot-Group Community-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('QA-Copilot', 'Group Community')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="QA-Copilot-name" placeholder="Card name...">
                            <input type="url" id="QA-Copilot-url" placeholder="Card link...">
                            <button onclick="addCard('QA-Copilot')">Add</button>
                        </div>
                    </div><div class="section" id="US-PROD-Green-section">
                        <div class="section-header">
                            <h2>US-PROD-Green</h2>
                            <button class="delete-section-btn" onclick="deleteSection('US-PROD-Green')">Delete Section</button>
                        </div>
                        <div class="container" id="US-PROD-Green-container"><div class="card" data-date="1741709210285" data-category="" style="background-color: rgb(239, 68, 68);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>API - Prod-Green</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-Green', 'API - Prod-Green')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-api-pipeline/actions/workflows/AZURE-PROD%20GREEN.yml" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-Green', 'API - Prod-Green')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-Green-API - Prod-Green-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-Green-API - Prod-Green-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-Green-API - Prod-Green-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-Green', 'API - Prod-Green')">Save</button>
                </div>
            </div><div class="card" data-date="1741709277261" data-category="" style="background-color: rgb(131, 24, 67);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US Prod Green</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-Green', 'US Prod Green')">
                        ⭐
                    </button>
                </div>
                <a href="https://prod1.bridger.lexisnexisrisk.com" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-Green', 'US Prod Green')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-Green-US Prod Green-client" value="LNSNegereUS ">
                        <button class="copy-btn" onclick="copyToClipboard('LNSNegereUS ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-Green-US Prod Green-userid" value="SNegere33 ">
                        <button class="copy-btn" onclick="copyToClipboard('SNegere33 ')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-Green-US Prod Green-password" value="Welcome1234!!@@@@@">
                        <button class="copy-btn" onclick="copyToClipboard('Welcome1234!!@@@@@')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-Green', 'US Prod Green')">Save</button>
                </div>
            </div><div class="card" data-date="1741709373249" data-category="" style="background-color: rgb(249, 115, 22);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>US Prod Smoke Test</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-Green', 'US Prod Smoke Test')">
                        ⭐
                    </button>
                </div>
                <a href="https://github.com/LexisNexis-RBA/bridger-selenium/actions/workflows/us-prod-smoke-test.yml" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-Green', 'US Prod Smoke Test')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-Green-US Prod Smoke Test-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-Green-US Prod Smoke Test-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-Green-US Prod Smoke Test-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-Green', 'US Prod Smoke Test')">Save</button>
                </div>
            </div><div class="card" data-date="1741709384820" data-category="" style="background-color: rgb(88, 140, 126);">
                <div style="display: flex; justify-content: space-between; align-items: center;">
                    <span>Jira Guidance</span>
                    <button class="favorite-btn " onclick="toggleFavorite('US-PROD-Green', 'Jira Guidance')">
                        ⭐
                    </button>
                </div>
                <a href="https://jira.rsi.lexisnexis.com/browse/XG5-82285" target="_blank">Visit</a>
                <button onclick="removeCard('US-PROD-Green', 'Jira Guidance')">Remove</button>
                <div class="tooltip">
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Client Name" id="US-PROD-Green-Jira Guidance-client" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="User ID" id="US-PROD-Green-Jira Guidance-userid" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <div style="display: flex; align-items: center; margin-bottom: 0.5rem;">
                        <input type="text" placeholder="Password" id="US-PROD-Green-Jira Guidance-password" value="">
                        <button class="copy-btn" onclick="copyToClipboard('')">Copy</button>
                    </div>
                    <button onclick="saveCardInfo('US-PROD-Green', 'Jira Guidance')">Save</button>
                </div>
            </div></div>
                        <div class="controls">
                            <input type="text" id="US-PROD-Green-name" placeholder="Card name...">
                            <input type="url" id="US-PROD-Green-url" placeholder="Card link...">
                            <button onclick="addCard('US-PROD-Green')">Add</button>
                        </div>
                    </div></body>
</html>
