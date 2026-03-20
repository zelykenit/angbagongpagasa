<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UPCAT 2027 | Full System Planner</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --up-maroon: #7B1113;
            --up-forest: #007A33;
            --gray-100: #f7fafc;
            --gray-300: #e2e8f0;
            --white: #ffffff;
        }

        body { font-family: 'Inter', sans-serif; margin: 0; background: var(--gray-100); color: #2d3748; }
        header { background: var(--up-maroon); color: white; padding: 1.5rem; text-align: center; font-weight: 700; letter-spacing: 1px; }

        /* REGISTRATION SCREEN */
        #loginScreen { max-width: 700px; margin: 40px auto; padding: 20px; }
        .auth-card { background: var(--white); padding: 30px; border-radius: 12px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); }
        .auth-card h2 { margin-top: 0; color: var(--up-maroon); border-bottom: 2px solid var(--gray-100); padding-bottom: 10px; text-align: center; }
        
        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-bottom: 15px; }
        input, select { width: 100%; padding: 12px; border: 1px solid var(--gray-300); border-radius: 8px; font-size: 0.9rem; box-sizing: border-box; background: white; }
        
        .choice-box { background: #fffcfc; border: 1px solid #f2e6e6; padding: 15px; border-radius: 8px; margin-bottom: 15px; }
        .choice-box label { font-weight: 700; font-size: 0.8rem; color: var(--up-maroon); text-transform: uppercase; display: block; margin-bottom: 10px; }
        .course-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }

        .btn-login { background: var(--up-forest); color: white; border: none; width: 100%; padding: 15px; border-radius: 8px; font-weight: 700; cursor: pointer; transition: 0.2s; font-size: 1rem; margin-top: 10px; }
        .btn-login:hover { background: #005f27; transform: translateY(-1px); }

        /* DASHBOARD */
        #dashboard { display: none; max-width: 1100px; margin: 30px auto; padding: 0 20px; }
        .stats-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 20px; margin-bottom: 25px; }
        .chart-card { background: var(--white); padding: 20px; border-radius: 12px; display: flex; flex-direction: column; align-items: center; justify-content: center; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        .welcome-card { background: var(--white); padding: 20px; border-radius: 12px; border-left: 6px solid var(--up-forest); box-shadow: 0 4px 6px rgba(0,0,0,0.05); }

        .subject-container { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 20px; }
        .subject-card { background: var(--white); padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); position: relative; border: 1px solid transparent; transition: 0.3s; }
        .subject-card:hover { border-color: var(--up-maroon); }
        
        .toggle-link { color: #718096; text-decoration: none; font-size: 0.85rem; cursor: pointer; font-weight: 600; display: block; margin-top: 10px; border: 1px solid var(--gray-300); padding: 5px; text-align: center; border-radius: 5px; }
        .toggle-link:hover { background: var(--gray-100); }

        .topic-list { display: none; margin-top: 15px; padding: 10px; background: var(--gray-100); border-radius: 8px; max-height: 250px; overflow-y: auto; }
        .topic-item { display: flex; align-items: center; font-size: 0.8rem; margin-bottom: 8px; cursor: pointer; }
        .topic-item input { width: auto; margin-right: 10px; accent-color: var(--up-maroon); }

        .prog-badge { position: absolute; top: 15px; right: 15px; background: var(--up-maroon); color: white; padding: 2px 8px; border-radius: 12px; font-size: 0.7rem; font-weight: 700; }
        canvas { max-width: 140px; max-height: 140px; }

        @media (max-width: 768px) { .stats-grid { grid-template-columns: 1fr; } .form-row, .course-grid { grid-template-columns: 1fr; } }
    </style>
</head>
<body>

<header>UPCAT 2027 ASPIRANT PORTAL</header>

<div id="loginScreen">
    <div class="auth-card">
        <h2>Study Plan Setup</h2>
        <div class="form-row">
            <input type="text" id="firstname" placeholder="First Name" oninput="this.value=this.value.toUpperCase()">
            <input type="text" id="surname" placeholder="Surname" oninput="this.value=this.value.toUpperCase()">
        </div>

        <div class="choice-box">
            <label>1st Choice Campus</label>
            <select id="campus1" onchange="populateCourses(1)">
                <option value="">Select Campus...</option>
                <option value="Diliman">UP Diliman</option>
                <option value="Manila">UP Manila</option>
                <option value="LosBanos">UP Los Baños</option>
                <option value="Baguio">UP Baguio</option>
                <option value="Visayas">UP Visayas</option>
                <option value="Cebu">UP Cebu</option>
                <option value="Mindanao">UP Mindanao</option>
                <option value="Tacloban">UP Tacloban</option>
            </select>
            <div id="course-grid-1" class="course-grid" style="margin-top:10px;"></div>
        </div>

        <div class="choice-box">
            <label>2nd Choice Campus</label>
            <select id="campus2" onchange="populateCourses(2)">
                <option value="">Select Campus...</option>
                <option value="Diliman">UP Diliman</option>
                <option value="Manila">UP Manila</option>
                <option value="LosBanos">UP Los Baños</option>
                <option value="Baguio">UP Baguio</option>
                <option value="Visayas">UP Visayas</option>
                <option value="Cebu">UP Cebu</option>
                <option value="Mindanao">UP Mindanao</option>
                <option value="Tacloban">UP Tacloban</option>
            </select>
            <div id="course-grid-2" class="course-grid" style="margin-top:10px;"></div>
        </div>

        <button class="btn-login" onclick="launchDashboard()">Start My Review Journey</button>
    </div>
</div>

<div id="dashboard">
    <div class="stats-grid">
        <div class="chart-card">
            <canvas id="overallChart"></canvas>
            <div style="margin-top: 10px; font-weight: 700; color: var(--up-maroon); font-size: 0.9rem;">Total Mastery</div>
        </div>
        <div class="welcome-card">
            <h2 id="welcomeText" style="margin:0; color: var(--up-maroon);">Future Isko</h2>
            <div id="choiceSummary" style="margin-top: 10px; line-height: 1.6;"></div>
        </div>
    </div>
    <div class="subject-container" id="subjectRoot"></div>
</div>

<script>
// COMPLETE UP SYSTEM COURSE DATABASE
const FULL_UP_DATABASE = {
    "Diliman": ["BA Anthropology", "BS Applied Physics", "BS Architecture", "BA Art Studies", "BS Biology", "BA Broadcast Media Arts & Studies", "BS Business Administration", "BS Business Administration & Accountancy", "BS Business Economics", "BS Chemical Engineering", "BS Chemistry", "BS Civil Engineering", "BS Computer Engineering", "BS Computer Science", "BS Economics", "BS Electrical Engineering", "BS Electronics Engineering", "B Elementary Education", "BA English Studies", "BA European Languages", "BS Family Life & Child Development", "BA Filipino at Panitikan ng Pilipinas", "BA Film", "B Fine Arts", "BS Food Technology", "BS Geodetic Engineering", "BS Geography", "BS Geology", "BA History", "BS Hotel, Restaurant & Institution Mgt", "BS Industrial Engineering", "BS Interior Design", "BA Journalism", "B Landscape Architecture", "B Library & Information Science", "BA Linguistics", "BA Malikhaing Pagsulat sa Filipino", "BS Materials Engineering", "BS Mathematics", "BS Mechanical Engineering", "BS Metallurgical Engineering", "BS Mining Engineering", "BA Philosophy", "B Physical Education", "BS Physics", "BA Political Science", "BA Psychology", "BS Psychology", "B Public Administration", "B Secondary Education", "BS Social Work", "BA Sociology", "BA Speech Communication", "B Sports Science", "BS Statistics", "BA Theater Arts", "BS Tourism"],
    "Manila": ["BS Applied Physics", "BA Behavioral Sciences", "BS Biochemistry", "BS Biology", "BS Computer Science", "D Dental Medicine", "BA Development Studies", "BS Nursing", "BS Occupational Therapy", "BA Organizational Communication", "BS Pharmaceutical Sciences", "BS Pharmacy", "BA Philippine Arts", "BS Physical Therapy", "BA Political Science", "BS Public Health", "BS Speech Pathology"],
    "LosBanos": ["BS Accountancy", "BS Agribusiness Mgt & Entrepreneurship", "BS Agricultural & Applied Economics", "BS Agricultural & Biosystems Engineering", "BS Agricultural Biotechnology", "BS Agricultural Chemistry", "BS Agriculture", "BS Applied Mathematics", "BS Applied Physics", "BS Biology", "BS Chemical Engineering", "BS Civil Engineering", "BA Communication Arts", "BS Computer Science", "BS Development Communication", "BS Economics", "BS Electrical Engineering", "BS Food Science & Technology", "BS Forestry", "BS Human Ecology", "BS Industrial Engineering", "BS Mathematics", "BS Mathematics & Science Teaching", "BS Mechanical Engineering", "BS Nutrition", "BA Philosophy", "BA Sociology", "BS Statistics", "D Veterinary Medicine"],
    "Baguio": ["BS Biology", "BA Communication", "BS Computer Science", "B Fine Arts", "BA Language & Literature", "BS Management Economics", "BS Mathematics", "BS Physics", "BA Social Sciences (Anthropology)", "BA Social Sciences (Economics)", "BA Social Sciences (History)"],
    "Visayas": ["BS Accountancy", "BS Applied Mathematics", "BS Biology", "BS Business Administration", "BS Chemical Engineering", "BS Chemistry", "BS Economics", "BS Computer Science", "BA Communication & Media Studies", "BA Community Development", "BS Fisheries", "BS Food Technology", "BA History", "BA Literature", "BS Management", "BA Political Science", "BA Psychology", "BS Public Health", "BS Statistics"],
    "Cebu": ["BS Biology", "BA Communication", "BS Computer Science", "B Fine Arts", "BS Management", "BS Mathematics", "BA Political Science", "BA Psychology", "BS Statistics"],
    "Mindanao": ["BS Agribusiness Economics", "BS Anthropology", "BS Applied Mathematics", "BS Architecture", "BS Biology", "BA Communication & Media Arts", "BS Computer Science", "BS Data Science", "BA English", "BS Food Technology", "B Sports Science"],
    "Tacloban": ["BS Accountancy", "BS Applied Mathematics", "BS Biology", "BS Computer Science", "BS Economics", "BA Literature", "BS Management", "BA Media Arts", "BA Political Science", "BA Psychology"]
};

const SUBJECT_CURRICULUM = [
    { title: "Language Proficiency", topics: ["Subject-Verb Agreement", "Correct Usage", "Sentence Construction", "Figures of Speech", "Vocabulary", "Punctuation", "Error Identification", "Parallelism", "Active & Passive Voice"] },
    { title: "Science", topics: ["Earth's Surface", "Plate Tectonics", "Solar System", "Cell Structure", "Genetics & Heredity", "Taxonomy", "States of Matter", "Gas Laws", "Atomic Theory", "Ecosystems"] },
    { title: "Mathematics", topics: ["Arithmetic Operations", "Prime Factorization", "GCF & LCM", "Pythagorean Theorem", "Linear Equations", "Quadratic Equations", "Functions & Graphs", "Trigonometric Ratios", "Probability", "Measures of Central Tendency"] },
    { title: "Reading Comprehension", topics: ["Main Idea & Topic Sentence", "Context Clues", "Inference & Conclusions", "Fact vs Opinion", "Author's Point of View", "Literary Criticism", "Poetry Analysis", "Comic/Editorial Interpretation"] }
];

function populateCourses(num) {
    const campus = document.getElementById('campus' + num).value;
    const grid = document.getElementById('course-grid-' + num);
    grid.innerHTML = "";
    if (campus && FULL_UP_DATABASE[campus]) {
        for (let i = 1; i <= 4; i++) {
            const sel = document.createElement('select');
            sel.id = `c${num}-choice-${i}`;
            sel.innerHTML = `<option value="">Course Choice ${i}</option>` + 
                FULL_UP_DATABASE[campus].map(c => `<option value="${c}">${c}</option>`).join('');
            grid.appendChild(sel);
        }
    }
}

function launchDashboard() {
    const fn = document.getElementById('firstname').value;
    const ln = document.getElementById('surname').value;
    const c1 = document.getElementById('campus1').value;
    const c2 = document.getElementById('campus2').value;

    if (!fn || !ln || !c1) return alert("Please enter your name and at least your 1st choice campus.");

    document.getElementById('loginScreen').style.display = 'none';
    document.getElementById('dashboard').style.display = 'block';
    document.getElementById('welcomeText').innerText = `Iskolar ng Bayan: ${fn} ${ln}`;
    
    // Summary Text
    let summaryHtml = `<strong>1st Choice:</strong> UP ${c1}<br>`;
    if (c2) summaryHtml += `<strong>2nd Choice:</strong> UP ${c2}`;
    document.getElementById('choiceSummary').innerHTML = summaryHtml;

    // Render Subjects
    const root = document.getElementById('subjectRoot');
    SUBJECT_CURRICULUM.forEach((sub, idx) => {
        const card = document.createElement('div');
        card.className = 'subject-card';
        card.innerHTML = `
            <span class="prog-badge" id="badge-${idx}">0%</span>
            <h3 style="margin:0; font-size:1rem;">${sub.title}</h3>
            <span class="toggle-link" id="link-${idx}" onclick="toggleTopics(${idx})">↓ View Topics</span>
            <div class="topic-list" id="list-${idx}">
                ${sub.topics.map(t => `<label class="topic-item"><input type="checkbox" onchange="refreshProgress(${idx})"> ${t}</label>`).join('')}
            </div>
        `;
        root.appendChild(card);
    });
    drawDonut(0);
}

function toggleTopics(id) {
    const list = document.getElementById('list-' + id);
    const link = document.getElementById('link-' + id);
    const isVisible = list.style.display === "block";
    list.style.display = isVisible ? "none" : "block";
    link.innerText = isVisible ? "↓ View Topics" : "↑ Hide Topics";
}

function refreshProgress(idx) {
    const list = document.getElementById('list-' + idx);
    const checks = list.querySelectorAll('input');
    const checked = list.querySelectorAll('input:checked').length;
    document.getElementById('badge-' + idx).innerText = Math.round((checked/checks.length)*100) + "%";
    
    // Overall Calc
    const all = document.querySelectorAll('.topic-item input');
    const allChecked = document.querySelectorAll('.topic-item input:checked').length;
    drawDonut(allChecked / all.length);
}

function drawDonut(percent) {
    const canvas = document.getElementById('overallChart');
    const ctx = canvas.getContext('2d');
    canvas.width = 300; canvas.height = 300;
    const cx = 150, cy = 150, r = 120;
    
    ctx.clearRect(0,0,300,300);
    ctx.beginPath();
    ctx.arc(cx, cy, r, 0, 2*Math.PI);
    ctx.strokeStyle = '#e2e8f0';
    ctx.lineWidth = 25;
    ctx.stroke();

    ctx.beginPath();
    ctx.arc(cx, cy, r, -Math.PI/2, (-Math.PI/2) + (2*Math.PI*percent));
    ctx.strokeStyle = '#7B1113';
    ctx.lineWidth = 25;
    ctx.lineCap = 'round';
    ctx.stroke();

    ctx.font = 'bold 55px Inter';
    ctx.fillStyle = '#7B1113';
    ctx.textAlign = 'center';
    ctx.fillText(Math.round(percent*100) + "%", cx, cy + 18);
}
</script>
</body>
</html>
