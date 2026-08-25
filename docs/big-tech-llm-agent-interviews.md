# 🏢 Big Tech LLM & Agentic AI Interview Prep

> **تنبيه مهم:** هذه أسئلة تدريبية أصلية مبنية على محاور متكررة في مقابلات ML/AI Engineering، وليست أسئلة مسرّبة أو ضمانًا لما ستسأله شركة بعينها. يختلف loop حسب الفريق والمستوى والدور؛ تحققي دائمًا من الوصف الوظيفي وتجربة المقابلة التي يشاركها recruiter.

## كيف تُقيّمين إجابتك؟

الإجابة القوية لا تذكر اسم framework فقط. ابدئي بتعريف المشكلة، ثم الافتراضات، ثم baseline، ثم المقياس، ثم trade-offs، ثم الفشل والأمان والتكلفة. هذا النمط متسق مع أسلوب التحضير الذي يركز على المعرفة والتصميم والتطبيق العملي في مراجع مقابلات ML.[^1]

## محاور Big Tech المتوقعة

| المحور | ما الذي يريد interviewer رؤيته؟ | دليل من Portfolio |
|---|---|---|
| Coding & CS | كود صحيح، تعقيد، testing، ووضوح | CLI أو tool مكتوبة باختبارات |
| ML Fundamentals | framing، leakage، metrics، generalization | Churn API مع error analysis |
| LLM Systems | retrieval، prompting، evals، latency، cost | Citation-first RAG |
| Agent Design | state، tools، planning، limits، fallback | Research Agent bounded |
| Production | observability، reliability، security، rollout | architecture + runbook |
| Product Sense | قيمة المستخدم، adoption، feedback loop | metric tree وsuccess criteria |
| Behavioral | ownership، ambiguity، failure، impact | 5 قصص STAR |

## أسئلة LLM Engineering

### Foundations and model behavior

1. ما الفرق بين pretraining وinstruction tuning وRLHF أو preference optimization؟ اشرحي ما الذي يتغير في كل مرحلة.
2. لماذا قد يعطي النموذج إجابة مقنعة لكنها خاطئة؟ صممي طريقة قياس وتقليل المشكلة بدل الاكتفاء بـ"prompt أفضل".
3. ما الفرق بين temperature وtop-p؟ متى تفضلين deterministic decoding؟
4. كيف تختارين model size أو provider عندما تكون لديكِ قيود latency وbudget وprivacy؟
5. ما الذي يجب تسجيله في production دون تخزين بيانات المستخدم الحساسة؟

### RAG and retrieval

6. صممي RAG لمستودع وثائق عربي/إنجليزي. حددي ingestion، parsing، chunking، metadata، embedding، retrieval، reranking، generation، citations.
7. كيف تفرّقين بين فشل retrieval وفشل generation؟
8. ما أثر chunk size وoverlap وquery rewriting؟ كيف تختبرين كل قرار؟
9. متى تستخدمين hybrid search بدل vector search وحده؟
10. كيف تتعاملين مع وثيقة محدثة أو متعارضة مع وثيقة قديمة؟
11. كيف تمنعين النظام من الإجابة بثقة عندما لا يوجد evidence كافٍ؟
12. صممي golden dataset لتقييم Arabic RAG، مع labels للـrelevance وfaithfulness وanswer correctness.
13. كيف تحافظين على access control عندما تختلف صلاحيات المستخدمين على الوثائق؟

### Evaluation and operations

14. ما الفرق بين offline evaluation وonline evaluation؟ وما metric الذي قد يخدعك؟
15. كيف تنشئين regression test تمنع prompt أو model update من خفض الجودة؟
16. كيف توازنين بين جودة الإجابة، latency، token cost، وcache hit rate؟
17. كيف تكتشفين prompt injection أو data exfiltration داخل سياق مسترجع؟
18. متى تستخدمين human review؟ وكيف تختارين عينة المراجعة؟

## أسئلة Agentic AI

### Architecture and decision-making

19. متى يكون workflow deterministic أفضل من agent؟ أعطي مثالًا لا يحتاج reasoning مفتوحًا.
20. صممي agent يقرأ issue، يبحث في وثائق، يقترح patch، ثم يطلب موافقة قبل فتح Pull Request.
21. ما الفرق بين state وmemory وcontext؟ وما الذي يجب أن يبقى بعد انتهاء المهمة؟
22. كيف تمنعين loop لا نهائي أو tool thrashing؟ حددي timeout وstep budget وtoken budget.
23. متى تستخدمين single agent، ومتى multi-agent؟ ما تكلفة التعقيد الإضافي؟
24. كيف تصممين fallback إذا فشل provider أو تعذر استدعاء tool؟
25. كيف تجعلين نتائج agent قابلة لإعادة الإنتاج قدر الإمكان؟

### Tools, permissions and MCP

26. كيف تصممين tool schema يقلل سوء الاستخدام؟ ناقشي types، validation، side effects، وidempotency.
27. لماذا تحتاج tool خطرة مثل حذف ملف أو إرسال بريد إلى human approval؟ صممي permission boundary.
28. ما الفرق بين function/tool calling وMCP؟ ومتى يفيد معيار موحد لربط التطبيقات بالأدوات والبيانات؟ توثيق MCP يصفه كمعيار مفتوح لهذا النوع من الاتصال.[^2]
29. كيف تصممين MCP server لقاعدة بيانات بحيث لا يصبح قناة لتسريب كل البيانات؟
30. كيف تسجلين trace يوضح قرار agent دون تسجيل أسرار أو chain-of-thought خاص؟

### Safety and evaluation

31. صممي red-team set لهجمات prompt injection، tool misuse، data poisoning، وindirect injection.
32. كيف تقيسين agent success عندما تكون المهمة متعددة الخطوات؟ عرّفي task success وtool correctness وpolicy compliance.
33. ماذا تفعلين إذا أعاد agent نتيجة صحيحة باستخدام tool غير مسموح؟
34. كيف تفرّقين بين agent autonomy المفيدة وautonomy التي تزيد المخاطر بلا قيمة؟
35. كيف تتعاملين مع تضارب تعليمات المستخدم وتعليمات النظام ومحتوى الوثائق؟

## System Design Prompts

### Prompt A — Enterprise Knowledge Agent

صممي مساعدًا داخليًا يجيب من 10 ملايين وثيقة، يدعم العربية والإنجليزية، ويعرض citations، مع صلاحيات per-document وSLO للزمن. ناقشي indexing، partitioning، retrieval، caching، evaluation، PII، monitoring، وcost.

### Prompt B — Support Resolution Agent

صممي agent يقرأ تذكرة دعم، يبحث في runbooks، يقترح ردًا، ويستطيع تنفيذ action آمن بعد موافقة الموظف. ناقشي state machine، human-in-the-loop، retries، audit log، rollback، وقياس resolution rate.

### Prompt C — Code Review Agent

صممي agent يستخدم repository tools لتحليل Pull Request. يجب ألا يكتب مباشرة إلى production، ويجب أن تكون ملاحظاته قابلة للتفسير. ناقشي sandbox، permissions، test execution، prompt injection في الكود، وfalse positives.

## إجابة نموذجية مختصرة

**السؤال:** كيف تقيسين RAG؟

**إجابة قوية:** أفصل مرحلتين. أولًا أقيس retrieval على golden set باستخدام recall@k وprecision أو nDCG مع فحص يدوي للعينات. ثانيًا أقيس generation عبر correctness وfaithfulness وcitation precision، مع مجموعة أسئلة لا تملك إجابة للتأكد من أن النظام يرفض بأمان. أربط ذلك بقياسات production مثل latency وcost وfallback rate، وأشغّل regression evaluation قبل كل تغيير في embedding أو prompt أو reranker.

## Checklist قبل المقابلة

- [ ] أستطيع رسم RAG وAgent architecture خلال 5 دقائق.
- [ ] أشرح baseline وmetric قبل ذكر framework.
- [ ] أذكر failure modes وfallback وrollback.
- [ ] أتناقش في latency والتكلفة والخصوصية.
- [ ] أشرح tool permissions وhuman approval.
- [ ] أملك مشروعين مع demo ونتائج موثقة.
- [ ] تدربت على coding وSQL وsystem design وSTAR.

## References

[^1]: [Introduction to Machine Learning Interviews — Chip Huyen](https://huyenchip.com/ml-interviews-book/).
[^2]: [What is the Model Context Protocol? — MCP Documentation](https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro).
