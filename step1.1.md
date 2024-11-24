نحتاج بيانات حتى ندرب عليها نموذج الذكاء الإصطناعي، من فين نجيب هذي البيانات وكيف شكلها؟
تركزينا في هذا الكتاب على بناء مايسمى بنماذج لغوية ضخمة،
Large Language Models (LLMs)
هذي النماذج تحتاج حجم كبير من البيانات النصية.
حأعطيك أمثلة لأماكن ممكن تحصل منها على هذي البيانات:
- ممكن تدخل ويكيبيديا وتنسخ كل النصوص وتحطها في ملف واحد
- ممكن  تدخل على الصحف السعودية وتنسخ مقالات الكتاب و تجمعها في ملف واحد
- تقدر تكتب كود يدخل تويتر ويجمع التغريدات وحفظها في ملف واحد

نحتاج نص طويل، مثلاً:
```
(غازي القصيبي، جريدة الوطن)
أول ما تفتحت عيناي عليه كان قويًا صاخبًا بالحياة. ومرت سنوات، وهزل وانحنى، ومرت سنوات أخرى، ومشيت وراء النعش مذهولًا، لا أكاد أصدق أن العملاق النابض بالحياة يحمل جسدًا ضئيلًا، بعيدًا عن الحياة.
قيل لي حين بدأت أعي ما حولي: «أبوك في الستين»، ولم يكن الرقم يعني شيئًا لي حينئذ. وكبرت قليلًا، وأدركت أن الستين ترتبط في الأذهان بالشيخوخة، وأصبت بالحيرة. كان أبي تجسيدًا للعنفوان، فكيف يجتمع عنفوان وكبر؟! كانت خطواته تهز الأرض، وتبتلع الدرج قفزًا، كان منتصبًا كالرمح، كان أوسم من رأيت من الرجال.
وقبل أن يودع الدنيا بأيام كان لقائي الأخير معه، كان قد تجاوز التسعين، بدا كأنه يعتذر بالضعف عن الحيوية التي لازمت شبابه وكهولته، كان يتجلد أمام الزوار ويصمد، يجلس بكامل هيئته، يخشى أن تخونه الذاكرة، أو ينزلق لسانه بجملة لا معنی لها. وبين المشاهد الأولى والمشاهد الأخيرة تومض مواقف وقصص، في البداية لم يكن غير وجود مهيب (ومخيف أحيانًا)، أقف عندما يجيء، أقبل يده كلما رأيته، أنظر إلى الأرض وهو يحدثني، في النهاية، أصبح الصديق الوديع، ظل الوجود مهيبًا (ولم يعد مخيفًا) ظللت أقبل يده كلما رأيته. أتحدث إليه وعيناي لا تفارقان وجهه.
...
```
رحم الله أديبنا الكبير غازي القصيبي، ورحم والدي ووالدتي وجميع موتى المسلمين

الجزء السابق من مقالة غازي القصيبي رحمه الله مكون تقريباً من ١٠٠٠ حرف، في حالة النماذج اللغوية الضخمة نحتاج أكثر من هذا بكثير،، نتكلم عن مليارات الحروف، حتى يتمكن النموذج من التعلم بشكل صحيح.

جمع هذي البيانات وترتيبها وتجهيزها عملية ماهي صعبة، لكنها شاقة وتحتاج جهد، لكن في ناس رهيبه جداً تعمل بشكل مستمر على جمع هذا النوع من البيانات وتجهيزها وترتيبها ونشرها حتى يستفيد منها الجميع، هذي البيانات عادة مبعثرة على الإنترنت، لكن مؤخراً 
HuggingFace
بدأت تصير المستودع الأكبر للبيانات ونماذج الذكاء الإصطناعي، وبدأت الناس الرهيبه تنشر البيانات على هذا الموقع وصار الوصول لها سهل.
الشركة كذلك وفرت مكتبة برمجية اسمها 
Datasets
تسمح لنا بتحميل البيانات و التعامل معها بشكل سريع.

في هذا الكتاب ، سنستخدم مجموعة بيانات فيها أكثر من ١٢٠٠ قصة باللغة العربية الدارجة، موجودة على هذا الرابط:
https://huggingface.co/datasets/arbml/Rewayatech

الآن، خلينا نكتب الكود إلي نحتاجه حتى نحمل البيانات.

```
# تحميل بيانات مجموعة القصص
rewayatech_ds = load_dataset("arbml/Rewayatech", split='train')
```
خلصنا!

هذا السطر يطلب من مكتبة Datasets تحميل البيانات، ويخزنها في المتغير rewayatech_ds.

تقدر تجرب تتفاعل مع المتغير rewayatech_ds، مثلاً:
```
# طباعة عدد القصص
print("عدد القصص:", len(rewayatech_ds))

# طباعة أول ١٠٠ حرف من أحد القصص
print(rewayatech_ds[2]['Text'][0:100])
```