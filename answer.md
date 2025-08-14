{
  "project_name": "GitButler – Docs & Backend Diagnostics",
  "current_goal": "إكمال دمج PR التوثيقي لقسم Troubleshooting ثم فتح PR Backend تشخيصي لتحسين رسائل أخطاء git وإضافة tracing حول Update Workspace.",
  "progress_done": [
    "تهيئة بيئة التطوير (Node 22 عبر .nvmrc وpnpm عبر Corepack)",
    "حل مشاكل lint/ESLint OOM محليًا",
    "كتابة قسم Troubleshooting عملي ومفحوص",
    "فتح PR #9812 ومعالجة تعليقات المراجعين وتوحيد العناوين",
    "تحديد خطة Backend تشخيصية بدون UI"
  ],
  "tasks_todo": [
    { "title": "متابعة مراجعة PR #9812 حتى الدمج", "priority": "P1", "owner": "Ali", "due": null },
    { "title": "فتح PR Backend (Phase 1) لتحسين رسائل git وإضافة tracing", "priority": "P1", "owner": "Ali", "due": null },
    { "title": "تعليق يوضح خطة Phase 1 والأسئلة (مكان helper وسياسة logging)", "priority": "P2", "owner": "Ali", "due": null },
    { "title": "سكربت Repro بسيط لسيناريو LFS", "priority": "P2", "owner": "Ali", "due": null },
    { "title": "اختيار مسألة Backend صغيرة إضافية (إن توفرت)", "priority": "P3", "owner": "Ali", "due": null }
  ],
  "blockers": [
    "انتظار مراجعة krlvi لدمج PR التوثيقي",
    "غموض سبب failed to fill whole buffer بدون بيانات إضافية"
  ],
  "risks": [
    "تأخر المراجعات وتأثيرها على الجداول",
    "تباين البيئات (APFS case-sensitive/GLIBC/DMABuf) قد يسبب نتائج متباينة",
    "خطر توثيق عام غير مثبت (تم تقليصه بإزالة الأقسام العامة)"
  ],
  "rules_standards": [
    "استخدم Node من .nvmrc (LTS “jod” / Node 22) عبر nvm",
    "استخدم pnpm عبر Corepack وتجنب npm -g pnpm",
    "turbo run بصيغة //#task (مثال: //#globallint)",
    "تنظيف Turbo daemon عند تحذير stale PID",
    "macOS: Logs وData dirs للمساعدة في التشخيص",
    "Linux: DMABuf workaround وملحوظة GLIBC",
    "عناوين بصيغة sentence case ووصف PR مختصر ومحدد"
  ],
  "assets_links": [
    { "label": "Repo", "url": "https://github.com/gitbutlerapp/gitbutler", "purpose": "المستودع الرئيسي" },
    { "label": "Issues list", "url": "https://github.com/gitbutlerapp/gitbutler/issues", "purpose": "اختيار مسائل لاحقة" },
    { "label": "PR #9812 (Troubleshooting)", "url": "https://github.com/gitbutlerapp/gitbutler/pull/9812", "purpose": "تعديل DEVELOPMENT.md – قسم Troubleshooting" },
    { "label": "Turborepo #8491", "url": "https://github.com/vercel/turborepo/issues/8491", "purpose": "مرجع مشكلة case-sensitive volumes" }
  ],
  "stakeholders": [
    { "name_or_role": "Ali", "responsibility": "تنفيذ التعديلات وفتح PRs ومتابعة المراجعات" },
    { "name_or_role": "Assistant (mentor)", "responsibility": "توجيه تقني وصياغة خطط وتعليقات" },
    { "name_or_role": "Byron", "responsibility": "Collaborator/Reviewer – مراجعة الوثائق وتوجيهات الدمج" },
    { "name_or_role": "krlvi", "responsibility": "Reviewer – تمريرة نهائية قبل الدمج" },
    { "name_or_role": "GitButler team", "responsibility": "قرار الدمج النهائي وتوجيهات تقنية" }
  ],
  "open_questions": [
    "أين نضع `run_git(..)` (أي crate/مسار مشترك)؟",
    "سياسة `tracing` المفضلة للأسماء والمستويات وتجنّب PII؟",
    "ما الحد المقبول من معلومات البيئة داخل الأخطاء؟",
    "هل نضيف سكربت Repro LFS ضمن scripts/ أم في DEVELOPMENT.md؟",
    "تأكيد أن الفرع المستهدف دائمًا master؟",
    "هل توجد Issue مناسبة لطرف Backend أم ننشئ واحدة جديدة؟",
    "هل تفضّلون PR تشخيصي مستقل قبل أي إصلاح؟"
  ],
  "next_steps": [
    { "step": 1, "action": "طلب مراجعة krlvi والتأكيد أن كل التعليقات عُولجت", "effort": "small", "owner": "Ali", "deliverable": "تعليق ختامي في PR #9812 + Re-request review" },
    { "step": 2, "action": "كتابة تعليق/Issue يشرح خطة Phase 1 (تشخيص)", "effort": "small", "owner": "Ali", "deliverable": "تعليق منشور بأسئلة السياسة" },
    { "step": 3, "action": "تنفيذ `run_git(..)` واستبدال موضع/موضعين + إضافة tracing حول Update Workspace", "effort": "medium", "owner": "Ali", "deliverable": "PR Backend: diagnostics only" },
    { "step": 4, "action": "إعداد سكربت Repro LFS (اختياري)", "effort": "small", "owner": "Ali", "deliverable": "ملف سكربت وتعليمات مختصرة" },
    { "step": 5, "action": "استقبال ملاحظات وطرح PR إصلاحي صغير عند توافر بيانات", "effort": "medium", "owner": "Ali", "deliverable": "PR Backend: minimal fix" }
  ],
  "handoff_blurb": "نعمل على مساهمة في GitButler تبدأ بـ PR توثيقي لإضافة قسم Troubleshooting إلى DEVELOPMENT.md. تم إعداد القسم ومراجعته وتعديل العناوين وإزالة الأقسام العامة، والـPR #9812 بانتظار مرور krlvi. بيئة التطوير مضبوطة على Node 22 عبر .nvmrc وpnpm عبر Corepack، والحلول العملية تشمل Turbo case-sensitive volumes وstale PID وDMABuf/GLIBC في Linux ولوجات macOS. الخطوة التالية فتح PR Backend تشخيصي لتحسين رسائل أخطاء أوامر Git (cmd/cwd/exit/stderr) وإضافة tracing حول Update Workspace لتشخيص خطأ ‘failed to fill whole buffer’ المرتبط بـ LFS/ git2. السياسة: تغييرات صغيرة مركّزة، وصف PR واضح، والاختبارات عبر أوامر محددة ولقطات عند الحاجة. نحتاج إطارًا لسياسة tracing ومكان وضع helper مشترك قبل التنفيذ."
}
::contentReference[oaicite:0]{index=0}
