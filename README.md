
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NightShift USA | Overnight Jobs</title>
<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f4f6fb;
  color: #172033;
}
header {
  background: #0b1220;
  color: white;
  padding: 22px 8%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo { font-size: 23px; font-weight: bold; }
.logo span { color: #a5b4fc; }
header a { color: white; text-decoration: none; }
.hero {
  background: linear-gradient(135deg,#101a35,#3730a3);
  color: white;
  padding: 70px 8%;
  text-align: center;
}
.hero h1 { font-size: clamp(32px,5vw,54px); margin: 0 0 16px; }
.hero p { color: #dbe4ff; font-size: 17px; }
.search {
  background: white;
  padding: 12px;
  max-width: 850px;
  margin: 28px auto 0;
  border-radius: 12px;
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}
.search input, .search select {
  flex: 1;
  min-width: 150px;
  padding: 14px;
  border: 1px solid #dce1eb;
  border-radius: 7px;
  font-size: 15px;
}
button {
  background: #4f46e5;
  color: white;
  border: 0;
  border-radius: 7px;
  padding: 13px 20px;
  cursor: pointer;
  font-weight: bold;
}
button:hover { background: #3730a3; }
main { max-width: 1100px; margin: 38px auto; padding: 0 20px; }
.heading { display:flex; justify-content:space-between; gap:12px; align-items:center; }
.jobs {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(260px,1fr));
  gap: 18px;
  margin-top: 22px;
}
.job {
  background: white;
  border: 1px solid #e5e9f2;
  border-radius: 12px;
  padding: 23px;
  box-shadow: 0 4px 15px #18213b08;
}
.tag {
  display: inline-block;
  background: #e8eaff;
  color: #3730a3;
  border-radius: 20px;
  padding: 6px 10px;
  font-size: 12px;
}
.job h3 { margin-bottom: 7px; }
.muted { color: #647087; font-size: 14px; }
.salary { font-weight: bold; margin: 18px 0; }
.job button { width: 100%; }
#message { color: #4f46e5; margin-top: 20px; }
footer {
  text-align: center;
  padding: 28px;
  color: #6b7280;
  font-size: 13px;
}
</style>
</head>
<body>
<header>
  <div class="logo">🌙 NightShift <span>USA</span></div>
  <a href="#jobs">Explore Jobs</a>
</header>

<section class="hero">
  <h1>Your Next Shift Starts Here</h1>
  <p>Explore overnight career opportunities across the United States.</p>
  <div class="search">
    <input id="keyword" placeholder="Job title or keyword">
    <select id="location">
      <option value="">All US locations</option>
      <option>New York</option>
      <option>Texas</option>
      <option>California</option>
      <option>Florida</option>
      <option>Illinois</option>
    </select>
    <button onclick="searchJobs()">Find Jobs</button>
  </div>
</section>

<main id="jobs">
  <div class="heading">
    <h2>Overnight Opportunities</h2>
    <span id="count" class="muted"></span>
  </div>
  <p class="muted">Example listings for website demonstration only.</p>
  <div class="jobs" id="jobList"></div>
  <p id="message"></p>
</main>

<footer>
  NightShift USA · Connecting people with overnight opportunities.
  <br><br>
  Demo website. Listings and pay ranges are illustrative,
  not verified job openings or salary offers.
</footer>

<script>
const jobs = [
  {title:"Overnight Customer Support",
   company:"Customer Care Example",
   location:"New York", pay:"$20–$25/hour",
   type:"Remote / Night shift"},
  {title:"Night Warehouse Associate",
   company:"Logistics Example",
   location:"Texas", pay:"$18–$23/hour",
   type:"On-site / Night shift"},
  {title:"Overnight IT Support",
   company:"Technology Example",
   location:"California", pay:"$25–$35/hour",
   type:"IT / Night shift"},
  {title:"Night Hotel Receptionist",
   company:"Hospitality Example",
   location:"Florida", pay:"$17–$22/hour",
   type:"On-site / Night shift"},
  {title:"Overnight Data Entry Clerk",
   company:"Office Services Example",
   location:"Illinois", pay:"$18–$24/hour",
   type:"Office / Night shift"},
  {title:"Night Security Officer",
   company:"Security Example",
   location:"Texas", pay:"$19–$26/hour",
   type:"On-site / Night shift"}
];

function renderJobs(list) {
  document.getElementById("jobList").innerHTML = list.map((job) => `
    <article class="job">
      <span class="tag">Night shift</span>
      <h3>${job.title}</h3>
      <p class="muted">${job.company}</p>
      <p>📍 ${job.location}, USA</p>
      <p class="muted">${job.type}</p>
      <p class="salary">${job.pay}</p>
      <button onclick="showDetails('${job.title.replace(/'/g, "\\'")}')">
        View Details
      </button>
    </article>
  `).join("");
  document.getElementById("count").textContent =
    list.length + " sample listings";
  document.getElementById("message").textContent =
    list.length ? "" : "No matching sample jobs. Try another search.";
}

function searchJobs() {
  const keyword = document.getElementById("keyword")
    .value.toLowerCase().trim();
  const location = document.getElementById("location").value;
  const filtered = jobs.filter(job =>
    (job.title + " " + job.company + " " + job.type)
      .toLowerCase().includes(keyword) &&
    (!location || job.location === location)
  );
  renderJobs(filtered);
}

function showDetails(title) {
  alert(title + "\\n\\nThis is a demonstration listing. " +
    "No employer or vacancy has been verified. " +
    "Connect a real job API to provide applications.");
}

document.getElementById("keyword").addEventListener("keydown", e => {
  if (e.key === "Enter") searchJobs();
});

renderJobs(jobs);
</script>
</body>
</html>
# Ranil-dsouza