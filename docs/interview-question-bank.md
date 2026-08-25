# 🎤 Interview Question Bank

## Fundamentals

1. ما الفرق بين bias وvariance؟ وكيف تكتشفين أن النموذج overfit؟
2. متى تكون Accuracy مضللة؟ قارنيها بـPrecision وRecall وPR-AUC.
3. كيف تمنعين data leakage في feature engineering وcross-validation؟
4. ما الفرق بين batch وonline inference؟ وما trade-off في latency والتكلفة؟
5. كيف تشرحين regularization لشخص غير تقني؟

## ML Case Study

1. عرّفي الهدف التجاري قبل اختيار النموذج.
2. حددي وحدة التنبؤ، نافذة الزمن، label، ومصدر كل feature.
3. ابدئي بـbaseline قابل للتفسير، ثم صممي ablation أو experiment.
4. اختاري offline metric مرتبطة بتكلفة أخطاء المنتج.
5. اشرحي كيف ستراقبين drift والجودة بعد الإطلاق.

## LLM / RAG

1. متى يكون fine-tuning غير مناسب مقارنةً بـRAG؟
2. كيف تختارين chunk size وoverlap؟
3. كيف تقيسين retrieval quality منفصلة عن answer quality؟
4. كيف تتعاملين مع prompt injection ومصادر غير موثوقة؟
5. كيف تخفضين latency وtoken cost مع الحفاظ على الجودة؟

## Agents & Automation

1. متى تختارين workflow deterministic بدل agent؟
2. كيف تمنعين agent من تنفيذ tool خطير دون موافقة؟
3. ما أهمية idempotency وretry مع webhooks؟
4. كيف تصممين timeout وbudget وfallback؟
5. ما الفرق بين tool calling وMCP؟

## System Design Prompt

صممي مساعدًا داخليًا يجيب من 100 ألف وثيقة عربية وإنجليزية، ويستطيع فتح ticket بعد موافقة المستخدم. ناقشي ingestion، retrieval، citations، permissions، queueing، evaluation، monitoring، PII، والـrollback.

## Behavioral Prompts

استخدمي STAR: **Situation → Task → Action → Result**. حضّري قصة عن مشروع فشل، قرار تحت غموض، اختلاف مع teammate، تحسين قابل للقياس، وموقف تعلمتِ فيه تقنية بسرعة.
