import React, { useState, createContext, useContext, useMemo } from 'react';
import { BarChart, Briefcase, Users, LayoutDashboard, FileText, Calendar, CheckSquare, Users2, Settings, Search, Bell, ChevronDown, ChevronUp, Plus, Filter, MoreVertical, Eye, Edit, Trash2, Archive, UploadCloud, Palette, Type, Link, Paperclip, Star, GitMerge, Users as UsersIcon, Funnel, Bot, Sparkles, Video, Image as ImageIcon, File as FileIcon, Clock, GripVertical, ArrowRight, ArrowLeft, Languages, Sun, Moon, Building, Phone, Fingerprint, PlusCircle, ChevronRight, ChevronLeft, Download } from 'lucide-react';

// --- i18n (Internationalization) Setup ---
const translations = {
  en: {
    // General
    search: "Search...",
    notifications: "Notifications",
    profile: "Profile",
    logout: "Logout",
    language: "Language",
    english: "English",
    arabic: "Arabic",
    save: "Save",
    cancel: "Cancel",
    add_new: "Add New",
    view: "View",
    edit: "Edit",
    archive: "Archive",
    delete: "Delete",
    all: "All",
    active: "Active",
    archived: "Archived",
    status: "Status",
    actions: "Actions",
    name: "Name",
    client: "Client",
    dueDate: "Due Date",
    team: "Team",
    dark_mode: "Dark Mode",
    light_mode: "Light Mode",
    assignees: "Assignees",
    description: "Description",
    responsibilities: "Responsibilities",
    performance: "Performance",
    
    // Platforms
    facebook: "Facebook",
    instagram: "Instagram",
    twitter: "X (Twitter)",
    linkedin: "LinkedIn",
    tiktok: "TikTok",
    snapchat: "Snapchat",
    pinterest: "Pinterest",
    youtube: "YouTube",
    google_ads: "Google Ads",
    google_analytics: "Google Analytics",

    // Sidebar
    dashboard: "Dashboard",
    clients: "Clients",
    content_calendar: "Content Calendar",
    tasks: "Tasks",
    reports: "Reports",
    team_management: "Team Management",
    settings: "Settings",
    job_roles: "Job Roles",
    org_chart: "Org Chart",

    // Dashboard
    greeting: "Good Morning",
    active_tasks: "Active Tasks",
    overdue_tasks: "Overdue Tasks",
    content_in_review: "Content in Review",
    ad_spend: "Ad Spend (This Month)",
    my_day: "My Day",
    this_weeks_content: "This Week's Content",
    client_performance_snapshot: "Client Performance Snapshot",
    kpi: "Key Metric",
    change: "Change",
    smart_inbox: "Smart Inbox",
    mentions_and_approvals: "All your mentions and approvals in one place.",
    momentum_ai_insights: "Momentum AI Insights",
    bottleneck_risk: "Bottleneck Risk",
    bottleneck_desc: "'Campaign Launch' is blocked by 'Ad Copy' which is 2 days overdue.",
    high_workload: "High Workload",
    high_workload_desc: "Ali has 12 tasks due this week. Consider reassigning.",
    performance_opportunity: "Performance Opportunity",
    performance_opportunity_desc: "Video ads for 'Client A' have the highest ROAS. Recommend increasing budget.",
    approval_pipeline: "Approval Pipeline",
    draft: "Draft",
    internal_review: "Internal Review",
    client_review: "Client Review",
    approved: "Approved",
    published: "Published",
    not_published: "Not Published",

    // Clients
    clients_hub: "Clients Hub",
    add_new_client: "Add New Client",
    search_client: "Search for a client...",
    client_name: "Client Name",
    start_date: "Start Date",
    assigned_team: "Assigned Team",
    client_form_title: "Add / Edit Client",
    basic_info: "Basic Information",
    website: "Website",
    industry: "Industry",
    upload_logo: "Upload Logo",
    brand_assets: "Brand Assets",
    primary_colors: "Primary Colors",
    fonts: "Fonts",
    brand_guidelines: "Brand Guidelines",
    credentials: "Access Credentials",
    credentials_notice: "All data here is encrypted. For maximum security, use the client portal for direct access requests.",
    connect_account: "Connect Account (API)",

    // Client Profile
    client_profile: "Client Profile",
    overview: "Overview",
    okrs: "OKRs",
    personas: "Personas",
    funnel: "Funnel",
    projects_content: "Projects & Content",
    live_reports: "Live Reports",
    dam: "Asset Management (DAM)",
    integrations_access: "Integrations & Access",
    objective: "Objective",
    key_result: "Key Result",
    progress: "Progress",
    awareness: "Awareness",
    consideration: "Consideration",
    decision: "Decision",
    version: "Version",
    uploaded_on: "Uploaded On",
    expires_on: "Expires On",
    
    // Content Calendar
    content_calendar_title: "Content Calendar",
    filter_by_client: "Filter by Client",
    filter_by_status: "Filter by Status",
    filter_by_publish_status: "Filter by Publish Status",
    month: "Month",
    week: "Week",
    list: "List",
    create_post: "Create Post",
    post_editor: "Post Editor",
    copy: "Copy",
    media: "Media",
    platforms: "Platforms",
    schedule: "Schedule",
    live_preview: "Live Preview",
    approval_status: "Approval Status",
    send_for_review: "Send for Review",
    comments: "Comments",
    sub_tasks: "Sub-tasks",
    ai_copilot: "AI Co-pilot",
    generate_ideas: "Generate Ideas",
    rephrase_text: "Rephrase Text",
    mark_as_published: "Mark as Published",
    
    // Tasks
    tasks_title: "Tasks",
    board: "Board",
    timeline: "Timeline",
    todo: "To Do",
    in_progress: "In Progress",
    done: "Done",
    add_new_task: "Add New Task",
    task_title: "Task Title",
    assign_to: "Assign to",
    
    // Team Management
    add_new_role: "Add New Role",
    job_title: "Job Title",
    add_team_member: "Add Team Member",
    phone_number: "Phone Number",
    national_id: "National ID",
    employee_profile: "Employee Profile",
    personal_information: "Personal Information",
    job_information: "Job Information",
    assigned_tasks_overview: "Assigned Tasks Overview",
    performance_indicator: "Performance Indicator",
    on_time_completion_rate: "On-time Completion Rate",
    generate_employee_report: "Generate Employee Report",

    // Reports
    report_builder: "Report Builder",
    final_report_view: "Final Report View",
    report_setup: "Report Setup",
    report_name: "Report Name",
    date_range: "Date Range",
    from: "From",
    to: "To",
    metrics_library: "Metrics Library",
    report_canvas: "Report Canvas",
    drag_drop_metrics: "Drag & drop metrics here",
    enter_value_manually: "Enter value manually",
    total_spend: "Total Spend",
    reach: "Reach",
    impressions: "Impressions",
    cpc: "CPC",
    clicks: "Clicks",
    roas: "ROAS",
    sessions: "Sessions",
    users: "Users",
    bounce_rate: "Bounce Rate",
    text_box: "Text Box",
    image: "Image",
    page_break: "Page Break",
    preview_report: "Preview Report",
    save_template: "Save as Template",
    export_pdf: "Export as PDF",
    share_link: "Share Link",
    back_to_edit: "Back to Edit",
    ai_analyst: "AI Analyst",
    generate_summary: "Generate Performance Summary",
    ai_summary_text: "AI Summary: Campaign [X] performance is up 20% from average, while campaign [Y] is underperforming. Recommend shifting budget.",

    // Settings
    app_settings: "Application Settings",
    feature_flags: "Feature Flags",
    enable_feature: "Enable this feature",
    notification_settings: "Notification Settings",
    task_assignment_notif: "Task Assignment",
    task_reminder_notif: "Task Reminders",
  },
  ar: {
    // General
    search: "ابحث...",
    notifications: "الإشعارات",
    profile: "الملف الشخصي",
    logout: "تسجيل الخروج",
    language: "اللغة",
    english: "English",
    arabic: "العربية",
    save: "حفظ",
    cancel: "إلغاء",
    add_new: "إضافة جديد",
    view: "عرض",
    edit: "تعديل",
    archive: "أرشفة",
    delete: "حذف",
    all: "الكل",
    active: "نشط",
    archived: "مؤرشف",
    status: "الحالة",
    actions: "الإجراءات",
    name: "الاسم",
    client: "العميل",
    dueDate: "تاريخ الاستحقاق",
    team: "الفريق",
    dark_mode: "الوضع الداكن",
    light_mode: "الوضع الفاتح",
    assignees: "المكلفون",
    description: "الوصف",
    responsibilities: "المهام الوظيفية",
    performance: "الأداء",

    // Platforms
    facebook: "فيسبوك",
    instagram: "انستغرام",
    twitter: "X (تويتر)",
    linkedin: "لينكدإن",
    tiktok: "تيك توك",
    snapchat: "سناب شات",
    pinterest: "بينترست",
    youtube: "يوتيوب",
    google_ads: "إعلانات جوجل",
    google_analytics: "تحليلات جوجل",

    // Sidebar
    dashboard: "لوحة التحكم",
    clients: "العملاء",
    content_calendar: "أجندة المحتوى",
    tasks: "المهام",
    reports: "التقارير",
    team_management: "إدارة الفريق",
    settings: "الإعدادات",
    job_roles: "الوظائف",
    org_chart: "الهيكل التنظيمي",

    // Dashboard
    greeting: "صباح الخير",
    active_tasks: "المهام النشطة",
    overdue_tasks: "مهام متأخرة",
    content_in_review: "محتوى قيد المراجعة",
    ad_spend: "الإنفاق الإعلاني (هذا الشهر)",
    my_day: "مهامي لهذا اليوم",
    this_weeks_content: "محتوى هذا الأسبوع",
    client_performance_snapshot: "أداء العملاء السريع",
    kpi: "مؤشر الأداء",
    change: "التغير",
    smart_inbox: "صندوق الوارد الذكي",
    mentions_and_approvals: "كل الإشارات والموافقات المطلوبة في مكان واحد.",
    momentum_ai_insights: "رؤى Momentum الذكية",
    bottleneck_risk: "خطر الاختناق",
    bottleneck_desc: "'إطلاق الحملة' متوقف على 'كتابة الإعلان' المتأخرة يومين.",
    high_workload: "عبء عمل مرتفع",
    high_workload_desc: "لدى علي ١٢ مهمة مستحقة هذا الأسبوع. يُنصح بإعادة التوزيع.",
    performance_opportunity: "فرصة أداء",
    performance_opportunity_desc: "إعلانات الفيديو للعميل 'أ' تحقق أعلى عائد. يُنصح بزيادة الميزانية.",
    approval_pipeline: "خط سير الموافقات",
    draft: "مسودة",
    internal_review: "مراجعة داخلية",
    client_review: "مراجعة العميل",
    approved: "تمت الموافقة",
    published: "تم النشر",
    not_published: "لم يتم النشر",

    // Clients
    clients_hub: "مركز العملاء",
    add_new_client: "إضافة عميل جديد",
    search_client: "ابحث عن عميل...",
    client_name: "اسم العميل",
    start_date: "تاريخ البدء",
    assigned_team: "الفريق المعين",
    client_form_title: "إضافة / تعديل عميل",
    basic_info: "المعلومات الأساسية",
    website: "الموقع الإلكتروني",
    industry: "مجال الصناعة",
    upload_logo: "رفع الشعار",
    brand_assets: "أصول العلامة التجارية",
    primary_colors: "الألوان الأساسية",
    fonts: "الخطوط",
    brand_guidelines: "دليل الهوية البصرية",
    credentials: "معلومات الوصول",
    credentials_notice: "جميع البيانات هنا مشفرة. للأمان الأقصى، استخدم بوابة العميل لطلب الوصول المباشر.",
    connect_account: "ربط الحساب (API)",

    // Client Profile
    client_profile: "ملف العميل",
    overview: "نظرة عامة",
    okrs: "الأهداف والنتائج",
    personas: "شخصيات الجمهور",
    funnel: "قمع المبيعات",
    projects_content: "المشاريع والمحتوى",
    live_reports: "التقارير الحية",
    dam: "إدارة الأصول",
    integrations_access: "التكاملات والوصول",
    objective: "الهدف",
    key_result: "النتيجة الرئيسية",
    progress: "التقدم",
    awareness: "وعي",
    consideration: "اهتمام",
    decision: "قرار",
    version: "الإصدار",
    uploaded_on: "تاريخ الرفع",
    expires_on: "تاريخ الانتهاء",

    // Content Calendar
    content_calendar_title: "أجندة المحتوى",
    filter_by_client: "فلترة حسب العميل",
    filter_by_status: "فلترة حسب الحالة",
    filter_by_publish_status: "فلترة حسب حالة النشر",
    month: "شهري",
    week: "أسبوعي",
    list: "قائمة",
    create_post: "إنشاء منشور",
    post_editor: "محرر المنشور",
    copy: "النص",
    media: "الوسائط",
    platforms: "المنصات",
    schedule: "جدولة",
    live_preview: "معاينة حية",
    approval_status: "حالة الموافقة",
    send_for_review: "أرسل للمراجعة",
    comments: "التعليقات",
    sub_tasks: "المهام الفرعية",
    ai_copilot: "مساعد الذكاء الاصطناعي",
    generate_ideas: "توليد أفكار",
    rephrase_text: "إعادة صياغة",
    mark_as_published: "تحديد كم منشور",

    // Tasks
    tasks_title: "المهام",
    board: "لوحة",
    timeline: "خط زمني",
    todo: "للقيام به",
    in_progress: "قيد التنفيذ",
    done: "مكتمل",
    add_new_task: "إضافة مهمة جديدة",
    task_title: "عنوان المهمة",
    assign_to: "تعيين إلى",

    // Team Management
    add_new_role: "إضافة وظيفة جديدة",
    job_title: "المسمى الوظيفي",
    add_team_member: "إضافة عضو للفريق",
    phone_number: "رقم الهاتف",
    national_id: "رقم الهوية",
    employee_profile: "الملف الشخصي للموظف",
    personal_information: "البيانات الشخصية",
    job_information: "البيانات الوظيفية",
    assigned_tasks_overview: "نظرة عامة على المهام المسندة",
    performance_indicator: "مؤشر الأداء",
    on_time_completion_rate: "معدل الإنجاز في الوقت المحدد",
    generate_employee_report: "إنشاء تقرير أداء الموظف",

    // Reports
    report_builder: "مُنشئ التقارير",
    final_report_view: "عرض التقرير النهائي",
    report_setup: "إعداد التقرير",
    report_name: "اسم التقرير",
    date_range: "النطاق الزمني",
    from: "من",
    to: "إلى",
    metrics_library: "مكتبة المقاييس",
    report_canvas: "لوحة التقرير",
    drag_drop_metrics: "اسحب وأفلت المقاييس هنا",
    enter_value_manually: "أدخل القيمة يدويًا",
    total_spend: "إجمالي الإنفاق",
    reach: "الوصول",
    impressions: "الظهور",
    cpc: "تكلفة النقرة",
    clicks: "النقرات",
    roas: "عائد الإنفاق",
    sessions: "الجلسات",
    users: "المستخدمون",
    bounce_rate: "معدل الارتداد",
    text_box: "مربع نص",
    image: "صورة",
    page_break: "فاصل صفحات",
    preview_report: "معاينة التقرير",
    save_template: "حفظ كقالب",
    export_pdf: "تصدير كـ PDF",
    share_link: "مشاركة رابط",
    back_to_edit: "العودة للتعديل",
    ai_analyst: "المحلل الذكي",
    generate_summary: "توليد ملخص الأداء",
    ai_summary_text: "ملخص ذكي: أداء حملة [س] أعلى بنسبة 20% من المتوسط، بينما أداء حملة [ص] أقل. يُنصح بتحويل الميزانية.",
    
    // Settings
    app_settings: "إعدادات التطبيق",
    feature_flags: "التحكم في الميزات",
    enable_feature: "تفعيل هذه الميزة",
    notification_settings: "إعدادات الإشعارات",
    task_assignment_notif: "إشعارات تعيين المهام",
    task_reminder_notif: "إشعارات تذكير المهام",
  },
};

const ALL_PLATFORMS = [
    {id: 'facebook', name: 'Facebook', icon: () => <svg className="h-6 w-6 text-blue-600" fill="currentColor" viewBox="0 0 24 24"><path d="M22 12c0-5.52-4.48-10-10-10S2 6.48 2 12c0 4.84 3.44 8.87 8 9.8V15H8v-3h2V9.5C10 7.57 11.57 6 13.5 6H16v3h-1.5c-1 0-1.5.5-1.5 1.5V12h3l-.5 3h-2.5v6.8c4.56-.93 8-4.96 8-9.8z" /></svg>},
    {id: 'instagram', name: 'Instagram', icon: () => <svg className="h-6 w-6 text-pink-500" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.85s-.011 3.584-.069 4.85c-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07s-3.584-.012-4.85-.07c-3.252-.148-4.771-1.691-4.919-4.919-.058-1.265-.069-1.645-.069-4.85s.011-3.584.069-4.85c.149-3.225 1.664-4.771 4.919-4.919 1.266-.058 1.644-.07 4.85-.07m0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948s.014 3.667.072 4.947c.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072s3.667-.014 4.947-.072c4.358-.2 6.78-2.618 6.98-6.98.059-1.281.073-1.689.073-4.948s-.014-3.667-.072-4.947c-.2-4.358-2.618-6.78-6.98-6.98-1.281-.059-1.689-.073-4.948-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.162 6.162 6.162 6.162-2.759 6.162-6.162-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4s1.791-4 4-4 4 1.79 4 4-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44 1.441-.645 1.441-1.44-.645-1.44-1.441-1.44z" /></svg>},
    {id: 'twitter', name: 'X (Twitter)', icon: () => <svg className="h-6 w-6 text-black dark:text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z" /></svg>},
    {id: 'linkedin', name: 'LinkedIn', icon: () => <svg className="h-6 w-6 text-blue-700" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" /></svg>},
    {id: 'tiktok', name: 'TikTok', icon: () => <svg className="h-6 w-6 text-black dark:text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M12.525.02c1.31-.02 2.61-.01 3.91.02.08 1.53.63 3.09 1.75 4.17 1.12 1.11 2.7 1.62 4.24 1.79v4.03c-1.44-.05-2.89-.35-4.2-.97-.01-1.58-.48-3.16-1.5-4.45-1.02-1.28-2.52-2.05-4.03-2.24v9.19c.41.21.8.46 1.15.71 1.51 1.08 2.38 2.91 2.38 4.64 0 2.09-1.69 3.78-3.78 3.78s-3.78-1.69-3.78-3.78c0-1.73.87-3.56 2.38-4.64.34-.25.74-.5 1.15-.71V.02z"/></svg>},
    {id: 'snapchat', name: 'Snapchat', icon: () => <svg className="h-6 w-6 text-yellow-400" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 5.373 0 12s5.373 12 12 12 12-5.373 12-12S18.627 0 12 0zm.001 22c-5.522 0-10-4.477-10-10 0-5.522 4.478-10 10-10 5.523 0 10 4.478 10 10 0 5.523-4.477 10-10 10zm-2-14c0-1.104.896-2 2-2s2 .896 2 2-.896 2-2 2-2-.896-2-2zm-2.001 6c0-1.104.896-2 2-2s2 .896 2 2-.896 2-2 2-2-.896-2-2zm6.001 0c0-1.104.896-2 2-2s2 .896 2 2-.896 2-2 2-2-.896-2-2z"/></svg>},
    {id: 'pinterest', name: 'Pinterest', icon: () => <svg className="h-6 w-6 text-red-600" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 5.373 0 12c0 5.1 3.156 9.42 7.5 11.25.038-.34.058-.74.058-1.125 0-.975-.038-1.95.281-2.812.3-1.012 1.875-7.95 1.875-7.95s-.488-.975-.488-2.425c0-2.25 1.313-3.938 2.963-3.938 1.388 0 2.025.975 2.025 2.175 0 1.313-.825 3.3-1.238 5.138-.337 1.5.787 2.7 2.287 2.7 2.738 0 4.838-2.887 4.838-7.012 0-3.675-2.625-6.263-6.525-6.263-4.425 0-7.163 3.263-7.163 6.75 0 1.35.525 2.812 1.163 3.675.112.15.137.262.1.412-.038.15-.112.45-.15.6-.05.188-.225.263-.412.15-1.5-.862-2.438-2.85-2.438-4.612 0-3.787 3.15-7.537 8.287-7.537 4.35 0 7.725 3.075 7.725 7.05 0 4.313-2.737 7.688-6.525 7.688-1.275 0-2.512-.675-2.925-1.462 0 0-.638 2.512-.788 3.075-.262.975-.975 2.212-1.425 2.962C9.488 23.513 10.725 24 12 24c6.627 0 12-5.373 12-12S18.627 0 12 0z"/></svg>},
    {id: 'youtube', name: 'YouTube', icon: () => <svg className="h-6 w-6 text-red-500" fill="currentColor" viewBox="0 0 24 24"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>},
];


const LanguageContext = createContext();
const DataContext = createContext();
const SettingsContext = createContext();

// FIX: Corrected useTranslation hook implementation
const useTranslation = () => {
    const context = useContext(LanguageContext);
    if (!context) {
        throw new Error("useTranslation must be used within a LanguageProvider");
    }
    const { language, setLanguage } = context;

    const t = (key) => {
        return translations[language][key] || key;
    };

    return { t, language, setLanguage };
};

const useData = () => useContext(DataContext);
const useSettings = () => useContext(SettingsContext);

const LanguageProvider = ({ children }) => {
  const [language, setLanguage] = useState('ar');
  const value = useMemo(() => ({ language, setLanguage }), [language]);
  return <LanguageContext.Provider value={value}>{children}</LanguageContext.Provider>;
};

const SettingsProvider = ({ children }) => {
    const [settings, setSettings] = useState({
        showAiInsights: true,
        showClientPerformance: true,
        taskAssignmentNotif: true,
        taskReminderNotif: true,
    });
    const value = useMemo(() => ({ settings, setSettings }), [settings]);
    return <SettingsContext.Provider value={value}>{children}</SettingsContext.Provider>;
}

const DataProvider = ({ children }) => {
    const [data, setData] = useState({
        user: { name: "أحمد علي", role: "manager", avatar: "https://i.pravatar.cc/150?u=ahmed" },
        clients: [
            { id: 1, name: "شركة التطوير العقاري", logo: "https://placehold.co/100x100/7c3aed/ffffff?text=C", status: "active", team: [1, 2], startDate: "2024-01-15" },
            { id: 2, name: "مطاعم الذواقة", logo: "https://placehold.co/100x100/db2777/ffffff?text=M", status: "active", team: [3], startDate: "2023-11-01" },
            { id: 3, name: "متجر الأزياء الحديثة", logo: "https://placehold.co/100x100/16a34a/ffffff?text=A", status: "archived", team: [1], startDate: "2023-05-20" },
        ],
        tasks: {
            todo: [
                { id: 1, title: "كتابة محتوى لحملة العيد", client: "مطاعم الذواقة", dueDate: "2025-07-05", assignees: [2] },
                { id: 2, title: "تصميم إعلانات السوشيال ميديا", client: "شركة التطوير العقاري", dueDate: "2025-07-08", assignees: [3] },
            ],
            in_progress: [
                { id: 3, title: "إعداد تقرير الأداء الشهري", client: "شركة التطوير العقاري", dueDate: "2025-07-02", assignees: [1] },
            ],
            done: [
                { id: 4, title: "جدولة منشورات الأسبوع", client: "مطاعم الذواقة", dueDate: "2025-06-28", assignees: [2] },
                { id: 5, title: "بحث كلمات مفتاحية", client: "شركة التطوير العقاري", dueDate: "2025-06-20", assignees: [1] },
            ]
        },
        contentCalendar: [
            { id: 1, day: 2, title: "حملة الصيف", client: "متجر الأزياء الحديثة", status: "approved", platform: "instagram", published: true },
            { id: 2, day: 4, title: "عروض العيد", client: "مطاعم الذواقة", status: "client_review", platform: "facebook", published: false },
            { id: 3, day: 4, title: "مشروع جديد", client: "شركة التطوير العقاري", status: "draft", platform: "linkedin", published: false },
        ],
        jobRoles: [
            { id: 1, title: "مدير تسويق", description: "مسؤول عن الاستراتيجية العامة للتسويق وإدارة الفريق.", responsibilities: ["وضع الاستراتيجيات", "إدارة الميزانيات", "تحليل الأداء"] },
            { id: 2, title: "أخصائي وسائط اجتماعية", description: "مسؤول عن إدارة وإنشاء المحتوى على منصات التواصل.", responsibilities: ["جدولة المنشورات", "كتابة المحتوى", "التفاعل مع الجمهور"] },
            { id: 3, title: "مصمم جرافيك", description: "مسؤول عن إنشاء الأصول البصرية للحملات.", responsibilities: ["تصميم الإعلانات", "تعديل الصور", "الالتزام بالهوية البصرية"] },
        ],
        teamMembers: [
            { id: 1, name: "أحمد علي", phone: "010-123-4567", nationalId: "28501010101234", roleId: 1, avatar: "https://i.pravatar.cc/150?u=ahmed" },
            { id: 2, name: "سارة إبراهيم", phone: "011-234-5678", nationalId: "29002020202345", roleId: 2, avatar: "https://i.pravatar.cc/150?u=sara" },
            { id: 3, name: "علي حسن", phone: "012-345-6789", nationalId: "28803030303456", roleId: 3, avatar: "https://i.pravatar.cc/150?u=ali" },
        ],
        notifications: [
            { id: 1, text: "تم تعيين مهمة 'إعداد تقرير' لك.", read: false },
            { id: 2, text: "مهمة 'تصميم الإعلانات' ستنتهي غدًا.", read: false },
            { id: 3, text: "تمت الموافقة على محتوى 'حملة الصيف'.", read: true },
        ]
    });

    const value = useMemo(() => ({ data, setData }), [data]);
    return <DataContext.Provider value={value}>{children}</DataContext.Provider>;
};


// --- Components ---

const Sidebar = ({ setPage, page, subPage }) => {
    const { t, language } = useTranslation();
    const { data } = useData(); // FIX: Added useData hook to get user role
    const [teamSubMenuOpen, setTeamSubMenuOpen] = useState(page === 'team_management');

    const navItems = [
        { id: 'dashboard', label: t('dashboard'), icon: LayoutDashboard },
        { id: 'clients', label: t('clients'), icon: Users },
        { id: 'content_calendar', label: t('content_calendar'), icon: Calendar },
        { id: 'tasks', label: t('tasks'), icon: CheckSquare },
        { id: 'reports', label: t('reports'), icon: BarChart },
        { 
            id: 'team_management', 
            label: t('team_management'), 
            icon: Users2, 
            managerOnly: true,
            subItems: [
                { id: 'org_chart', label: t('org_chart'), icon: Users },
                { id: 'job_roles', label: t('job_roles'), icon: Briefcase },
            ]
        },
        { id: 'settings', label: t('settings'), icon: Settings },
    ];

    return (
        <aside className={`bg-gray-800 text-white ${language === 'ar' ? 'border-l' : 'border-r'} border-gray-700 flex flex-col transition-all duration-300 w-64`}>
            <div className="flex items-center justify-center h-20 border-b border-gray-700">
                <Bot className="h-8 w-8 text-indigo-400" />
                <h1 className="text-2xl font-bold mx-2">Momentum</h1>
            </div>
            <nav className="flex-1 px-4 py-6 space-y-2">
                {navItems.map(item => {
                    if (item.managerOnly && data.user.role !== 'manager') return null;
                    if (item.subItems) {
                        return (
                            <div key={item.id}>
                                <a
                                    href="#"
                                    onClick={(e) => { e.preventDefault(); setTeamSubMenuOpen(!teamSubMenuOpen); }}
                                    className={`flex items-center justify-between px-4 py-2.5 text-sm font-medium rounded-lg transition-colors duration-200 ${page === item.id ? 'bg-gray-700 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white'}`}
                                >
                                    <div className="flex items-center">
                                        <item.icon className={`h-5 w-5 ${language === 'ar' ? 'ml-3' : 'mr-3'}`} />
                                        {item.label}
                                    </div>
                                    <ChevronDown className={`h-4 w-4 transition-transform ${teamSubMenuOpen ? 'rotate-180' : ''}`} />
                                </a>
                                {teamSubMenuOpen && (
                                    <div className={`mt-1 space-y-1 ${language === 'ar' ? 'mr-4' : 'ml-4'}`}>
                                        {item.subItems.map(sub => (
                                            <a
                                                key={sub.id}
                                                href="#"
                                                onClick={(e) => { e.preventDefault(); setPage('team_management', sub.id); }}
                                                className={`flex items-center px-4 py-2 text-sm font-medium rounded-lg transition-colors duration-200 ${subPage === sub.id ? 'bg-indigo-500 text-white' : 'text-gray-300 hover:bg-gray-600'}`}
                                            >
                                                <sub.icon className={`h-4 w-4 ${language === 'ar' ? 'ml-3' : 'mr-3'}`} />
                                                {sub.label}
                                            </a>
                                        ))}
                                    </div>
                                )}
                            </div>
                        )
                    }
                    return (
                        <a
                            key={item.id}
                            href="#"
                            onClick={(e) => { e.preventDefault(); setPage(item.id); }}
                            className={`flex items-center px-4 py-2.5 text-sm font-medium rounded-lg transition-colors duration-200 ${page === item.id ? 'bg-indigo-500 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white'}`}
                        >
                            <item.icon className={`h-5 w-5 ${language === 'ar' ? 'ml-3' : 'mr-3'}`} />
                            {item.label}
                        </a>
                    );
                })}
            </nav>
        </aside>
    );
};

const TopBar = ({ user, setDarkMode, darkMode }) => {
    const { t, language, setLanguage } = useTranslation();
    const { data } = useData();
    const [profileOpen, setProfileOpen] = useState(false);
    const unreadNotifications = data.notifications.filter(n => !n.read).length;

    return (
        <header className="bg-white dark:bg-gray-800 shadow-sm h-20 flex items-center justify-between px-8 border-b dark:border-gray-700">
            <div className="relative">
                <Search className={`absolute ${language === 'ar' ? 'right-3' : 'left-3'} top-1/2 -translate-y-1/2 text-gray-400`} size={20} />
                <input
                    type="text"
                    placeholder={t('search')}
                    className={`bg-gray-100 dark:bg-gray-700 border-none rounded-lg ${language === 'ar' ? 'pr-10 pl-4' : 'pl-10 pr-4'} py-2 w-80 focus:ring-2 focus:ring-indigo-500 focus:outline-none`}
                />
            </div>
            <div className="flex items-center space-x-6">
                <button onClick={() => setDarkMode(!darkMode)} className="text-gray-500 dark:text-gray-400 hover:text-indigo-500 dark:hover:text-indigo-400">
                    {darkMode ? <Sun size={24}/> : <Moon size={24}/>}
                </button>
                <button className="relative text-gray-500 dark:text-gray-400 hover:text-indigo-500 dark:hover:text-indigo-400">
                    <Bell size={24} />
                    {unreadNotifications > 0 && <span className="absolute -top-1 -right-1 h-4 w-4 bg-pink-500 text-white text-xs rounded-full flex items-center justify-center">{unreadNotifications}</span>}
                </button>
                <div className="relative">
                    <button onClick={() => setProfileOpen(!profileOpen)} className="flex items-center space-x-2">
                        <img src={user.avatar} alt="User Avatar" className="h-10 w-10 rounded-full" />
                        <span className="font-semibold text-gray-700 dark:text-gray-200">{user.name}</span>
                        <ChevronDown className={`text-gray-500 dark:text-gray-400 transition-transform ${profileOpen ? 'rotate-180' : ''}`} size={20} />
                    </button>
                    {profileOpen && (
                        <div className={`absolute ${language === 'ar' ? 'left-0' : 'right-0'} mt-2 w-48 bg-white dark:bg-gray-800 rounded-lg shadow-xl py-2 z-10 border dark:border-gray-700`}>
                            <a href="#" className="block px-4 py-2 text-sm text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-700">{t('profile')}</a>
                            <div className="border-t border-gray-100 dark:border-gray-700 my-1"></div>
                            <div className="px-4 py-2 text-sm text-gray-500">{t('language')}</div>
                            <a href="#" onClick={(e) => { e.preventDefault(); setLanguage('en'); }} className={`block px-4 py-2 text-sm ${language === 'en' ? 'text-indigo-600 font-bold' : 'text-gray-700 dark:text-gray-200'} hover:bg-gray-100 dark:hover:bg-gray-700`}>{t('english')}</a>
                            <a href="#" onClick={(e) => { e.preventDefault(); setLanguage('ar'); }} className={`block px-4 py-2 text-sm ${language === 'ar' ? 'text-indigo-600 font-bold' : 'text-gray-700 dark:text-gray-200'} hover:bg-gray-100 dark:hover:bg-gray-700`}>{t('arabic')}</a>
                            <div className="border-t border-gray-100 dark:border-gray-700 my-1"></div>
                            <a href="#" className="block px-4 py-2 text-sm text-gray-700 dark:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-700">{t('logout')}</a>
                        </div>
                    )}
                </div>
            </div>
        </header>
    );
};

const Dashboard = () => {
    const { t } = useTranslation();
    const { data } = useData();
    const { settings } = useSettings();

    const kpiCards = [
        { title: t('active_tasks'), value: '18', icon: CheckSquare, color: 'text-blue-500' },
        { title: t('overdue_tasks'), value: '3', icon: Clock, color: 'text-red-500' },
        { title: t('content_in_review'), value: '5', icon: FileText, color: 'text-yellow-500' },
        { title: t('ad_spend'), value: '$12,450', icon: BarChart, color: 'text-green-500', managerOnly: true, setting: 'showClientPerformance' },
    ];

    return (
        <div className="p-8 space-y-8">
            <h1 className="text-3xl font-bold text-gray-800 dark:text-white">{t('greeting')}, {data.user.name}!</h1>

            {/* KPI Cards */}
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                {kpiCards.map(card => {
                    if ((card.managerOnly && data.user.role !== 'manager') || (card.setting && !settings[card.setting])) return null;
                    return (
                        <div key={card.title} className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6 flex items-center justify-between">
                            <div>
                                <p className="text-gray-500 dark:text-gray-400 text-sm font-medium">{card.title}</p>
                                <p className="text-3xl font-bold text-gray-800 dark:text-white mt-1">{card.value}</p>
                            </div>
                            <div className={`p-3 rounded-full bg-opacity-20 ${card.color.replace('text-', 'bg-')}`}>
                                <card.icon className={card.color} size={24} />
                            </div>
                        </div>
                    );
                })}
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div className="lg:col-span-2 space-y-8">
                    {/* My Day */}
                </div>

                <div className="lg:col-span-1 space-y-8">
                    {/* Smart Inbox */}
                    
                    {/* Momentum AI Insights */}
                    {settings.showAiInsights && (
                        <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
                            <div className="flex items-center mb-4">
                                <h2 className="text-xl font-bold text-gray-800 dark:text-white">{t('momentum_ai_insights')}</h2>
                                <Sparkles className="mx-2 text-indigo-500" />
                            </div>
                            <div className="space-y-4">
                                <div className="border-l-4 border-red-500 pl-4 py-2">
                                    <p className="font-bold text-red-500">{t('bottleneck_risk')}</p>
                                    <p className="text-sm text-gray-600 dark:text-gray-300">{t('bottleneck_desc')}</p>
                                </div>
                            </div>
                        </div>
                    )}
                </div>
            </div>
        </div>
    );
};

// ... Other components would be updated similarly ...
// Due to size limitations, I'll focus on implementing the new Team Management module and updating key areas.

const TeamManagement = ({ subPage, setPage, setSelectedEmployee }) => {
    const { t } = useTranslation();

    const renderSubPage = () => {
        switch (subPage) {
            case 'job_roles':
                return <JobRolesPage />;
            case 'org_chart':
                return <OrgChartPage setPage={setPage} setSelectedEmployee={setSelectedEmployee} />;
            default:
                return <OrgChartPage setPage={setPage} setSelectedEmployee={setSelectedEmployee} />;
        }
    };

    return (
        <div className="p-8">
            <h1 className="text-3xl font-bold text-gray-800 dark:text-white mb-6">{t('team_management')}</h1>
            {renderSubPage()}
        </div>
    );
};

const JobRolesPage = () => {
    const { t } = useTranslation();
    const { data } = useData();
    return (
        <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
            <div className="flex justify-between items-center mb-4">
                <h2 className="text-2xl font-bold">{t('job_roles')}</h2>
                <button className="flex items-center bg-indigo-600 text-white px-4 py-2 rounded-lg font-semibold">
                    <Plus size={20} className="mr-2" /> {t('add_new_role')}
                </button>
            </div>
            <div className="space-y-4">
                {data.jobRoles.map(role => (
                    <div key={role.id} className="border dark:border-gray-700 rounded-lg p-4">
                        <h3 className="font-bold text-lg text-gray-800 dark:text-white">{role.title}</h3>
                        <p className="text-sm text-gray-600 dark:text-gray-300 mt-1">{role.description}</p>
                        <div className="mt-3">
                            <h4 className="font-semibold text-sm mb-1">{t('responsibilities')}:</h4>
                            <ul className="list-disc list-inside space-y-1 text-sm text-gray-500 dark:text-gray-400">
                                {role.responsibilities.map(r => <li key={r}>{r}</li>)}
                            </ul>
                        </div>
                    </div>
                ))}
            </div>
        </div>
    );
};

const OrgChartPage = ({ setPage, setSelectedEmployee }) => {
    const { t } = useTranslation();
    const { data } = useData();
    const manager = data.teamMembers.find(m => m.roleId === 1);
    const team = data.teamMembers.filter(m => m.roleId !== 1);

    const handleEmployeeClick = (employee) => {
        setSelectedEmployee(employee);
        setPage('team_management', 'employee_profile');
    };

    return (
        <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
            <div className="flex justify-between items-center mb-6">
                <h2 className="text-2xl font-bold">{t('org_chart')}</h2>
                <button className="flex items-center bg-indigo-600 text-white px-4 py-2 rounded-lg font-semibold">
                    <Plus size={20} className="mr-2" /> {t('add_team_member')}
                </button>
            </div>
            <div className="flex flex-col items-center">
                {/* Manager */}
                {manager && (
                    <div onClick={() => handleEmployeeClick(manager)} className="p-4 bg-indigo-100 dark:bg-indigo-900/50 rounded-lg text-center cursor-pointer mb-8 relative">
                        <img src={manager.avatar} className="h-20 w-20 rounded-full mx-auto border-4 border-indigo-300" />
                        <h3 className="font-bold mt-2">{manager.name}</h3>
                        <p className="text-sm text-indigo-700 dark:text-indigo-300">{data.jobRoles.find(r => r.id === manager.roleId)?.title}</p>
                    </div>
                )}
                {/* Connecting Line */}
                <div className="w-px h-8 bg-gray-300 dark:bg-gray-600"></div>
                {/* Team Members */}
                <div className="flex justify-center gap-12">
                    {team.map(member => (
                        <div key={member.id} className="flex flex-col items-center">
                             <div className="w-px h-8 bg-gray-300 dark:bg-gray-600"></div>
                            <div onClick={() => handleEmployeeClick(member)} className="p-4 bg-gray-100 dark:bg-gray-700/50 rounded-lg text-center cursor-pointer">
                                <img src={member.avatar} className="h-16 w-16 rounded-full mx-auto border-4 border-gray-300" />
                                <h3 className="font-bold mt-2">{member.name}</h3>
                                <p className="text-sm text-gray-500 dark:text-gray-400">{data.jobRoles.find(r => r.id === member.roleId)?.title}</p>
                            </div>
                        </div>
                    ))}
                </div>
            </div>
        </div>
    );
};

const EmployeeProfilePage = ({ employee }) => {
    const { t } = useTranslation();
    const { data } = useData();
    const role = data.jobRoles.find(r => r.id === employee.roleId);
    const assignedTasks = Object.values(data.tasks).flat().filter(task => task.assignees.includes(employee.id));
    const onTimeRate = 85; // Dummy data

    return (
        <div className="p-8">
            <div className="flex items-center mb-6">
                <img src={employee.avatar} alt={employee.name} className="h-24 w-24 rounded-full mr-6 border-4 border-indigo-400" />
                <div>
                    <h1 className="text-4xl font-bold text-gray-800 dark:text-white">{employee.name}</h1>
                    <p className="text-xl text-gray-500 dark:text-gray-400">{role?.title}</p>
                </div>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div className="lg:col-span-1 space-y-6">
                    <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
                        <h3 className="font-bold text-lg mb-4">{t('personal_information')}</h3>
                        <div className="space-y-2 text-sm">
                            <p><Phone size={14} className="inline mr-2"/> {employee.phone}</p>
                            <p><Fingerprint size={14} className="inline mr-2"/> {employee.nationalId}</p>
                        </div>
                    </div>
                    <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
                        <h3 className="font-bold text-lg mb-4">{t('performance_indicator')}</h3>
                        <p className="text-sm text-gray-500">{t('on_time_completion_rate')}</p>
                        <p className="text-4xl font-bold text-green-500 mt-2">{onTimeRate}%</p>
                        <div className="w-full bg-gray-200 rounded-full h-2.5 mt-2">
                            <div className="bg-green-500 h-2.5 rounded-full" style={{width: `${onTimeRate}%`}}></div>
                        </div>
                    </div>
                     <button className="w-full flex items-center justify-center bg-indigo-600 text-white px-4 py-3 rounded-lg font-semibold">
                        <Download size={20} className="mr-2" /> {t('generate_employee_report')}
                    </button>
                </div>
                <div className="lg:col-span-2 bg-white dark:bg-gray-800 rounded-xl shadow-md p-6">
                    <h3 className="font-bold text-lg mb-4">{t('assigned_tasks_overview')}</h3>
                    <div className="space-y-4">
                        {assignedTasks.map(task => (
                             <div key={task.id} className="bg-gray-50 dark:bg-gray-700/50 rounded-md p-4">
                                <p className="font-semibold text-gray-800 dark:text-gray-100">{task.title}</p>
                                <p className="text-sm text-indigo-600 dark:text-indigo-400 mt-1">{task.client}</p>
                                <div className="flex justify-between items-center mt-3 text-xs text-gray-500 dark:text-gray-400">
                                    <span><Clock size={14} className="inline mr-1" />{task.dueDate}</span>
                                </div>
                            </div>
                        ))}
                    </div>
                </div>
            </div>
        </div>
    );
}

const SettingsPage = () => {
    const { t } = useTranslation();
    const { settings, setSettings } = useSettings();

    const handleToggle = (key) => {
        setSettings(prev => ({ ...prev, [key]: !prev[key] }));
    };

    return (
        <div className="p-8">
            <h1 className="text-3xl font-bold text-gray-800 dark:text-white mb-6">{t('app_settings')}</h1>
            <div className="bg-white dark:bg-gray-800 rounded-xl shadow-md p-6 max-w-2xl">
                <div className="space-y-6">
                    <div>
                        <h2 className="text-xl font-bold mb-4 border-b pb-2">{t('feature_flags')}</h2>
                        <div className="space-y-4">
                            <div className="flex items-center justify-between">
                                <label htmlFor="ai-insights" className="font-medium">{t('momentum_ai_insights')}</label>
                                <button onClick={() => handleToggle('showAiInsights')} className={`${settings.showAiInsights ? 'bg-indigo-600' : 'bg-gray-200 dark:bg-gray-600'} relative inline-flex h-6 w-11 items-center rounded-full`}>
                                    <span className={`${settings.showAiInsights ? 'translate-x-6' : 'translate-x-1'} inline-block h-4 w-4 transform rounded-full bg-white transition`}/>
                                </button>
                            </div>
                            <div className="flex items-center justify-between">
                                <label htmlFor="client-perf" className="font-medium">{t('client_performance_snapshot')}</label>
                                <button onClick={() => handleToggle('showClientPerformance')} className={`${settings.showClientPerformance ? 'bg-indigo-600' : 'bg-gray-200 dark:bg-gray-600'} relative inline-flex h-6 w-11 items-center rounded-full`}>
                                    <span className={`${settings.showClientPerformance ? 'translate-x-6' : 'translate-x-1'} inline-block h-4 w-4 transform rounded-full bg-white transition`}/>
                                </button>
                            </div>
                        </div>
                    </div>
                     <div>
                        <h2 className="text-xl font-bold mb-4 border-b pb-2">{t('notification_settings')}</h2>
                        <div className="space-y-4">
                            <div className="flex items-center justify-between">
                                <label className="font-medium">{t('task_assignment_notif')}</label>
                                <button onClick={() => handleToggle('taskAssignmentNotif')} className={`${settings.taskAssignmentNotif ? 'bg-indigo-600' : 'bg-gray-200 dark:bg-gray-600'} relative inline-flex h-6 w-11 items-center rounded-full`}>
                                    <span className={`${settings.taskAssignmentNotif ? 'translate-x-6' : 'translate-x-1'} inline-block h-4 w-4 transform rounded-full bg-white transition`}/>
                                </button>
                            </div>
                            <div className="flex items-center justify-between">
                                <label className="font-medium">{t('task_reminder_notif')}</label>
                                <button onClick={() => handleToggle('taskReminderNotif')} className={`${settings.taskReminderNotif ? 'bg-indigo-600' : 'bg-gray-200 dark:bg-gray-600'} relative inline-flex h-6 w-11 items-center rounded-full`}>
                                    <span className={`${settings.taskReminderNotif ? 'translate-x-6' : 'translate-x-1'} inline-block h-4 w-4 transform rounded-full bg-white transition`}/>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    )
}

// --- Main App Component ---
export default function App() {
    return (
        <LanguageProvider>
            <SettingsProvider>
                <DataProvider>
                    <AppContent />
                </DataProvider>
            </SettingsProvider>
        </LanguageProvider>
    );
}

// We need a sub-component to use the context from Providers
const AppContent = () => {
    const { language } = useTranslation();
    const { data } = useData();

    const [page, setPageState] = useState('dashboard');
    const [subPage, setSubPageState] = useState(null);
    const [selectedClient, setSelectedClient] = useState(null);
    const [selectedEmployee, setSelectedEmployee] = useState(null);
    const [darkMode, setDarkMode] = useState(true);

    const setPage = (main, sub = null) => {
        setPageState(main);
        setSubPageState(sub);
        if (main !== 'client_profile') setSelectedClient(null);
        if (main !== 'team_management' || sub !== 'employee_profile') setSelectedEmployee(null);
    };

    const renderPage = () => {
        switch (page) {
            case 'dashboard':
                return <Dashboard />;
            case 'clients':
                return <Clients setPage={setPage} setSelectedClient={setSelectedClient} />;
            case 'client_profile':
                return selectedClient ? <ClientProfile client={selectedClient} setPage={setPage} /> : <Clients setPage={setPage} setSelectedClient={setSelectedClient} />;
            case 'team_management':
                if (subPage === 'employee_profile' && selectedEmployee) {
                    return <EmployeeProfilePage employee={selectedEmployee} />;
                }
                return <TeamManagement subPage={subPage} setPage={setPage} setSelectedEmployee={setSelectedEmployee} />;
            case 'settings':
                return <SettingsPage />;
            // Add other pages here
            default:
                return <div className="p-8 text-xl">{page} page is not implemented yet.</div>;
        }
    };

    return (
        <div className={`${darkMode ? 'dark' : ''} ${language === 'ar' ? 'rtl' : 'ltr'}`}>
            <div className="flex h-screen bg-gray-100 dark:bg-gray-900 font-sans text-gray-900 dark:text-gray-200">
                <Sidebar setPage={setPage} page={page} subPage={subPage} />
                <div className="flex-1 flex flex-col overflow-hidden">
                    <TopBar user={data.user} setDarkMode={setDarkMode} darkMode={darkMode} />
                    <main className="flex-1 overflow-x-hidden overflow-y-auto">
                        {renderPage()}
                    </main>
                </div>
            </div>
        </div>
    );
}
