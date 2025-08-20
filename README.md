<!doctype html>
<html lang="vi">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Hồ sơ năng lực – Doanh nghiệp</title>
    <meta name="description" content="Mẫu giao diện hồ sơ năng lực (company profile) thuần HTML/CSS, responsive." />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #ffffff;
            --bg-soft: #f8fafc; /* slate-50 */
            --text: #0f172a;    /* slate-900 */
            --muted: #64748b;   /* slate-500/600 */
            --line: #e2e8f0;    /* slate-200 */
            --brand: #0f172a;   /* primary */
            --radius: 16px;
            --shadow: 0 8px 24px rgba(2, 6, 23, 0.06);
        }
        * { box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        body { margin:0; font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, Noto Sans, sans-serif; color: var(--text); background: linear-gradient(#f8fafc, #fff); }
        a { color: inherit; text-decoration: none; }
        img { display:block; max-width:100%; height:auto; }
        .container { width:100%; max-width: 1120px; margin: 0 auto; padding: 0 20px; }
        .btn { display:inline-flex; align-items:center; gap:8px; padding: 12px 18px; border-radius: 999px; font-weight:600; border:1px solid transparent; box-shadow: 0 1px 2px rgba(0,0,0,.04); }
        .btn-primary { background: var(--brand); color:#fff; }
        .btn-ghost { background:#fff; border-color: var(--line); color: var(--text); }
        .card { background:#fff; border:1px solid var(--line); border-radius: var(--radius); box-shadow: var(--shadow); }
        .muted { color: var(--muted); }

        /* Header */
        header { position: sticky; top:0; z-index: 50; backdrop-filter: blur(8px); background: rgba(255,255,255,.7); border-bottom:1px solid var(--line); }
        .nav { display:flex; align-items:center; justify-content:space-between; height:64px; }
        .brand { display:flex; align-items:center; gap:10px; font-weight:700; }
        .logo { width:36px; height:36px; border-radius: 14px; display:grid; place-items:center; background: var(--brand); color:#fff; font-size: 14px; }
        .nav-links { display:flex; gap:24px; align-items:center; }
        .nav a { color: #334155; font-size:14px; }
        .menu-btn { display:none; width:40px; height:40px; border:1px solid var(--line); border-radius:12px; background:#fff; }
        .mobile-menu { display:none; border-top:1px solid var(--line); }
        .mobile-menu a { display:block; padding: 12px 20px; color:#334155; }

        /* Hero */
        .hero { padding: 72px 0 28px; }
        .grid { display:grid; gap: 20px; }
        .cols-12 { grid-template-columns: repeat(12, minmax(0,1fr)); }
        .col-7 { grid-column: span 7; }
        .col-5 { grid-column: span 5; }

        .stats { display:grid; grid-template-columns:repeat(4,1fr); gap:16px; margin-top: 24px; }
        .stat { padding:16px; border-radius: 16px; border:1px solid var(--line); background:#fff; box-shadow: 0 1px 2px rgba(0,0,0,.03); }
        .stat .val { font-size: 28px; font-weight:700; }
        .stat .lab { font-size: 12px; color: var(--muted); margin-top: 6px; }

        .feature-box { border-radius: var(--radius); background: linear-gradient(135deg, #0f172a, #334155); padding: 6px; box-shadow: var(--shadow); }
        .feature-inner { height:100%; border-radius: calc(var(--radius) - 6px); background:#fff; display:grid; place-items:center; padding: 32px; text-align:center; }

        /* Sections */
        section { padding: 64px 0; }
        h1 { font-size: clamp(28px, 3.5vw, 48px); line-height: 1.1; margin: 0; }
        h2 { font-size: clamp(22px, 2.5vw, 32px); margin: 0; }
        h3 { font-size: 18px; margin: 0; }
        p { color:#475569; }

        /* Services */
        .services { display:grid; grid-template-columns: repeat(3, 1fr); gap:16px; }
        .service { padding:20px; }
        .icon { width:40px; height:40px; border-radius:12px; background:#f1f5f9; display:grid; place-items:center; color:#334155; margin-bottom: 10px; }

        /* Capabilities */
        .caps { display:grid; grid-template-columns: repeat(3, 1fr); gap:16px; margin-top: 24px; }
        .cap { display:flex; gap:10px; align-items:center; padding:14px; border:1px solid var(--line); border-radius: 16px; background:#fff; }
        .check { width:24px; height:24px; border-radius: 8px; background: var(--brand); color:#fff; display:grid; place-items:center; font-size:12px; }

        /* Projects */
        .projects { display:grid; grid-template-columns: repeat(4, 1fr); gap:16px; margin-top: 16px; }
        .project { overflow:hidden; border-radius: 16px; border:1px solid var(--line); background:#fff; box-shadow: var(--shadow); }
        .project .thumb { aspect-ratio: 4/3; overflow:hidden; }
        .project img { width:100%; height:100%; object-fit:cover; transition: transform .5s ease; }
        .project:hover img { transform: scale(1.06); }
        .project .meta { padding: 14px; }
        .tag { color: var(--muted); font-size: 12px; }

        /* Timeline */
        .timeline { display:grid; grid-template-columns: repeat(4, 1fr); gap:16px; margin-top:16px; }
        .time { padding: 16px; border:1px solid var(--line); border-radius:16px; background:#fff; }
        .time .year { font-weight:700; }
        .time .txt { font-size: 14px; color:#475569; margin-top:6px; }

        /* Clients & Testimonials */
        .chips { display:flex; flex-wrap:wrap; gap:10px; margin-top: 14px; }
        .chip { padding: 8px 14px; border:1px solid var(--line); border-radius: 14px; background:#fff; box-shadow: 0 1px 2px rgba(0,0,0,.03); }
        .quotes { display:grid; gap:12px; }
        .quote { padding: 16px; border:1px solid var(--line); border-radius: 16px; background:#fff; }
        .quote blockquote { margin:0; color:#475569; font-size: 14px; }
        .quote figcaption { margin-top: 8px; font-size: 12px; color: var(--muted); }

        /* Contact */
        form { display:grid; grid-template-columns: repeat(2, 1fr); gap: 12px; }
        label { font-size: 12px; color: var(--muted); display:block; margin-bottom:6px; }
        input, textarea { width:100%; padding: 10px 12px; border:1px solid var(--line); border-radius: 12px; font: inherit; }
        textarea { resize: vertical; }
        .form-row { display:block; }
        .form-actions { display:flex; align-items:center; justify-content:space-between; grid-column: span 2; }

        /* Footer */
        footer { border-top:1px solid var(--line); padding: 24px 0; font-size: 13px; color: var(--muted); }

        /* Responsive */
        @media (max-width: 1024px) {
            .col-7, .col-5 { grid-column: span 12; }
            .projects { grid-template-columns: repeat(2, 1fr); }
            .timeline { grid-template-columns: repeat(2, 1fr); }
        }
        @media (max-width: 768px) {
            .nav-links { display:none; }
            .menu-btn { display:block; }
            .hero { padding-top: 48px; }
            .services { grid-template-columns: 1fr; }
            .caps { grid-template-columns: 1fr; }
            .projects { grid-template-columns: 1fr; }
            .stats { grid-template-columns: repeat(2,1fr); }
            form { grid-template-columns: 1fr; }
            .form-actions { grid-column: auto; }
        }
    </style>
</head>
<body>
<!-- Header -->
<header>
    <div class="container nav">
        <a class="brand" href="#">
            <span class="logo">LN</span>
            <span>Songda11</span>
        </a>
        <nav class="nav-links" aria-label="Primary">
            <a href="#gioi-thieu">Giới thiệu</a>
            <a href="#nang-luc">Năng lực</a>
            <a href="#du-an">Dự án</a>
            <a href="#khach-hang">Khách hàng</a>
            <a href="#lien-he" class="btn btn-primary">Nhận báo giá</a>
        </nav>
        <button id="menuBtn" class="menu-btn" aria-label="Mở menu">☰</button>
    </div>
    <div id="mobileMenu" class="mobile-menu container">
        <a href="#gioi-thieu">Giới thiệu</a>
        <a href="#nang-luc">Năng lực</a>
        <a href="#du-an">Dự án</a>
        <a href="#khach-hang">Khách hàng</a>
        <a href="#lien-he">Liên hệ</a>
    </div>
</header>

<!-- Hero -->
<section class="hero">
    <div class="container grid cols-12" style="align-items:center; gap: 24px;">
        <div class="col-7">
            <h1>Hồ sơ năng lực <span class="muted">doanh nghiệp</span></h1>
            <p style="margin-top:12px; max-width: 640px;">Chúng tôi cung cấp giải pháp công nghệ trọn gói, từ tư vấn chiến lược đến vận hành hệ thống, giúp doanh nghiệp tăng trưởng bền vững.</p>
            <div style="margin-top:18px; display:flex; gap:10px; flex-wrap:wrap;">
                <a class="btn btn-primary" href="#du-an">Xem dự án</a>
                <a class="btn btn-ghost" href="#lien-he">Liên hệ nhanh</a>
            </div>
            <div class="stats">
                <div class="stat"><div class="val">10+</div><div class="lab">Năm kinh nghiệm</div></div>
                <div class="stat"><div class="val">120+</div><div class="lab">Dự án hoàn thành</div></div>
                <div class="stat"><div class="val">80+</div><div class="lab">Khách hàng</div></div>
                <div class="stat"><div class="val">98%</div><div class="lab">Tỷ lệ hài lòng</div></div>
            </div>
        </div>
        <div class="col-5">
            <div class="feature-box">
                <div class="feature-inner">
                    <div style="max-width: 380px;">
                        <div style="width:64px;height:64px;border-radius:14px;background:var(--brand);color:#fff;display:grid;place-items:center;margin:0 auto;font-weight:700;">★</div>
                        <p style="margin-top:12px;">"Đồng hành số hóa cùng doanh nghiệp Việt – hiệu quả, nhanh gọn, bền vững."</p>
                        <div class="muted" style="margin-top:6px; font-size:12px;">Slogan/giá trị cốt lõi</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Giới thiệu -->
<section id="gioi-thieu">
    <div class="container grid" style="grid-template-columns: repeat(12,1fr); gap: 20px; align-items:start;">
        <div style="grid-column: span 5;">
            <h2>Về chúng tôi</h2>
            <p style="margin-top:8px;">Songda11.</p>
            <ul class="muted" style="margin-top:10px; padding-left: 18px;">
                <li>Quy trình Agile minh bạch</li>
                <li>Đội ngũ chứng chỉ quốc tế</li>
                <li>Hệ sinh thái đối tác tin cậy</li>
            </ul>
        </div>
        <div style="grid-column: span 7;">
            <div class="services">
                <div class="card service">
                    <div class="icon">🗂️</div>
                    <h3>Tư vấn & Chiến lược</h3>
                    <p class="muted">Phân tích nhu cầu, xây dựng lộ trình triển khai tối ưu chi phí.</p>
                </div>
                <div class="card service">
                    <div class="icon">🧩</div>
                    <h3>Thiết kế & Phát triển</h3>
                    <p class="muted">Thiết kế UI/UX tinh gọn, code chuẩn SEO, hiệu năng cao.</p>
                </div>
                <div class="card service">
                    <div class="icon">🔧</div>
                    <h3>Vận hành & Bảo trì</h3>
                    <p class="muted">Giám sát 24/7, nâng cấp định kỳ, SLA rõ ràng.</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Năng lực -->
<section id="nang-luc" style="background: var(--bg-soft);">
    <div class="container">
        <h2>Năng lực cốt lõi</h2>
        <div class="caps">
            <div class="cap"><span class="check">✓</span>Thiết kế hệ thống chịu tải cao</div>
            <div class="cap"><span class="check">✓</span>Triển khai Cloud (AWS/Azure/GCP)</div>
            <div class="cap"><span class="check">✓</span>Bảo mật & tuân thủ tiêu chuẩn</div>
            <div class="cap"><span class="check">✓</span>Tối ưu SEO/Hiệu năng Web</div>
            <div class="cap"><span class="check">✓</span>Phân tích dữ liệu & BI</div>
            <div class="cap"><span class="check">✓</span>Tự động hoá quy trình RPA</div>
        </div>
    </div>
</section>

<!-- Dự án -->
<section id="du-an">
    <div class="container" style="display:flex; align-items:end; justify-content:space-between; gap: 16px;">
        <h2>Dự án tiêu biểu</h2>
        <a href="#" class="muted" style="font-size:14px;">Xem tất cả →</a>
    </div>
    <div class="container projects">
        <article class="project">
            <div class="thumb">
                <img alt="Hệ thống ERP" src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?q=80&w=1200&auto=format&fit=crop"/>
            </div>
            <div class="meta">
                <div class="tag">Doanh nghiệp</div>
                <h3>Hệ thống ERP</h3>
            </div>
        </article>
        <article class="project">
            <div class="thumb">
                <img alt="E-Commerce" src="https://images.unsplash.com/photo-1517245386807-bb43f82c33c4?q=80&w=1200&auto=format&fit=crop"/>
            </div>
            <div class="meta">
                <div class="tag">E‑Commerce</div>
                <h3>Ứng dụng Thương mại điện tử</h3>
            </div>
        </article>
        <article class="project">
            <div class="thumb">
                <img alt="Data & BI" src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?q=80&w=1200&auto=format&fit=crop"/>
            </div>
            <div class="meta">
                <div class="tag">Data & BI</div>
                <h3>Nền tảng Phân tích dữ liệu</h3>
            </div>
        </article>
        <article class="project">
            <div class="thumb">
                <img alt="Website Thương hiệu" src="https://images.unsplash.com/photo-1502882705085-cb9f4fe6cf7c?q=80&w=1200&auto=format&fit=crop"/>
            </div>
            <div class="meta">
                <div class="tag">Marketing</div>
                <h3>Website Thương hiệu</h3>
            </div>
        </article>
    </div>
</section>

<!-- Timeline -->
<section style="background: var(--bg-soft);">
    <div class="container">
        <h2>Cột mốc phát triển</h2>
        <div class="timeline">
            <div class="time"><div class="year">2016</div><div class="txt">Thành lập doanh nghiệp</div></div>
            <div class="time"><div class="year">2018</div><div class="txt">Đạt 50 dự án triển khai</div></div>
            <div class="time"><div class="year">2021</div><div class="txt">Mở rộng đội ngũ &gt; 50 nhân sự</div></div>
            <div class="time"><div class="year">2024</div><div class="txt">Ra mắt bộ giải pháp SaaS</div></div>
        </div>
    </div>
</section>

<!-- Khách hàng & Nhận xét -->
<section id="khach-hang">
    <div class="container" style="display:grid; grid-template-columns: repeat(12,1fr); gap: 20px; align-items:start;">
        <div style="grid-column: span 7;">
            <h2>Khách hàng tiêu biểu</h2>
            <div class="chips">
                <div class="chip">Acme</div>
                <div class="chip">NovaTech</div>
                <div class="chip">GreenBee</div>
                <div class="chip">Astral</div>
                <div class="chip">Lumio</div>
                <div class="chip">Vertex</div>
            </div>
        </div>
        <div style="grid-column: span 5;">
            <h3 style="margin-bottom:10px;">Khách hàng nói gì?</h3>
            <div class="quotes">
                <figure class="quote">
                    <blockquote>“Đội ngũ chuyên nghiệp, tiến độ đúng cam kết và hỗ trợ rất nhanh.”</blockquote>
                    <figcaption>Nguyễn Văn A • Giám đốc CNTT</figcaption>
                </figure>
                <figure class="quote">
                    <blockquote>“Thiết kế đẹp, dễ dùng, chuyển đổi tăng rõ rệt sau 3 tháng.”</blockquote>
                    <figcaption>Trần Thị B • Marketing Lead</figcaption>
                </figure>
            </div>
        </div>
    </div>
</section>

<!-- Liên hệ -->
<section id="lien-he" style="background: var(--bg-soft);">
    <div class="container" style="display:grid; grid-template-columns: repeat(12,1fr); gap: 20px;">
        <div style="grid-column: span 5;">
            <h2>Liên hệ hợp tác</h2>
            <p class="muted">Điền thông tin để nhận tư vấn trong 24h. Chúng tôi sẽ liên hệ qua email hoặc điện thoại.</p>
            <ul class="muted" style="margin-top:10px; padding-left: 18px;">
                <li>📍 Songda11, TP.HN</li>
                <li>✉️ contact@songda11.com.vn</li>
                <li>☎️ 0900 000 000</li>
            </ul>
        </div>
        <div style="grid-column: span 7;">
            <form onsubmit="event.preventDefault(); alert('Đã gửi yêu cầu!');" class="card" style="padding: 16px;">
                <div class="form-row">
                    <label for="name">Họ và tên</label>
                    <input id="name" placeholder="Nguyễn Văn A" required />
                </div>
                <div class="form-row">
                    <label for="email">Email</label>
                    <input id="email" type="email" placeholder="you@company.com" required />
                </div>
                <div class="form-row">
                    <label for="phone">Số điện thoại</label>
                    <input id="phone" placeholder="090..." />
                </div>
                <div class="form-row">
                    <label for="company">Doanh nghiệp</label>
                    <input id="company" placeholder="Công ty ABC" />
                </div>
                <div class="form-row" style="grid-column: span 2;">
                    <label for="need">Nhu cầu</label>
                    <textarea id="need" rows="4" placeholder="Mô tả ngắn gọn nhu cầu của bạn..."></textarea>
                </div>
                <div class="form-actions">
                    <label style="display:inline-flex; align-items:center; gap:8px; font-size:12px; color: var(--muted);">
                        <input id="agree" type="checkbox" required /> Tôi đồng ý với chính sách bảo mật
                    </label>
                    <button class="btn btn-primary" type="submit">Gửi yêu cầu</button>
                </div>
            </form>
        </div>
    </div>
</section>

<!-- Footer -->
<footer>
    <div class="container" style="display:flex; align-items:center; justify-content:space-between; gap: 12px; flex-wrap:wrap;">
        <div>© <span id="year"></span> Songda11. All rights reserved.</div>
        <div>Điều khoản • Bảo mật • Cookie</div>
    </div>
</footer>

<script>
    // Year
    document.getElementById('year').textContent = new Date().getFullYear();
    // Mobile menu toggle
    const btn = document.getElementById('menuBtn');
    const menu = document.getElementById('mobileMenu');
    btn.addEventListener('click', ()=>{
        menu.style.display = menu.style.display === 'block' ? 'none' : 'block';
    });
    // Close mobile menu when clicking a link
    menu.querySelectorAll('a').forEach(a=>a.addEventListener('click', ()=>{ menu.style.display='none'; }));
</script>
</body>
</html>
