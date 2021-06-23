# Thai Supreme Court Cases (TSCC) Dataset for ALQAC 2021

This is the dataset first appeared in the paper "Predicting Judicial Decisions of Criminal Cases from Thai Supreme Court Using Bi-directional GRU with Attention Mechanism" presented at the 5th Asian Conference on Defense Technology (ACDT 2018) in Hanoi, Vietnam. You can find the original dataset, its source and explanation at [[1]](https://github.com/KevinMercury/tscc-dataset).

However, exclusively for the 2021 Automated Legal Question Answering Competition (ALQAC 2021) [[2]](https://www.jaist.ac.jp/is/labs/nguyen-lab/home/alqac-2021/), TSCC has been altered from the csv version to that of JSON. As a result, this repository consists of two JSON files that will be used for the competition.

## tscc_alqac2021_law.json
This file has a big JSON array storing JSON objects of law mentioned in the question file. However, as we have only one law which is the Criminal Code (CC), the JSON array will have only one JSON Object of law.

JSON Object of Criminal Code has two keys. The "id" key contains the initial of the law, while "articles" key stores the JSON array of all legal provisions related to the Criminal Code and tscc_alqac2021_question.train.json. By the way, the format of this file will be showed below:

```
[
  {
    "id": "CC", # Initial stands for the Criminal Code
    "articles": [ # JSON array of each section in the law
      {
        "id": "CC-001(1)-00", # Law section ID that will be mentioned in the question file
        "text": "ในประมวลกฎหมายนี้ (๑) “โดยทุจริต” หมายความว่า เพื่อแสวงหาประโยชน์ที่มิควรได้โดยชอบด้วยกฎหมายสำหรับตนเองหรือผู้อื่น" #Law section text
      },
      ...
    ]
  }
]
```

## tscc_alqqac2021_question.train.json
This file  has a big JSON array which stores all legal questions. Each question will be a JSON object consists of question id, text, label, year and relevant_articles. Please note that relevant_articles will store all legal provisions related to that question and linked to the JSON file of law.

Here is the format of this question file:

```
[
  {
    "question_id": "q-1", # Question ID
    "text": "จำเลยกับพวกร่วมกันใช้อาวุธปืนยิงผู้ตายถูกที่ด้านหลัง กระสุนปืนตัดบริเวณไขสันหลังขาด ผู้ตายเป็นอัมพาตตั้งแต่เอวจนจดเท้าและถึงแก่ความตายสืบเนื่องมาจากบาดแผลที่ถูกยิงและภาวะติดเชื้ออย่างรุนแรงหลังจากเกิดเหตุ 9 เดือนเศษ  แม้จะเนื่องจากการรักษาไม่ดีจนบาดแผลติดเชื้อ ", # Question Text in Thai
    "relevant_articles": [ # JSON Array of Relevant Articles which can be found in the JSON file of law.
      {
        "law_id": "CC", # Initial ID of Law
        "article_id": "CC-288-00" # Law section ID
      },
      {
        "law_id": "CC",
        "article_id": "CC-083-00"
      },
      {
        "law_id": "CC",
        "article_id": "CC-063-00"
      }
    ],
    "label": true, # Question Label in boolean format
    "year": 2528 # Year of Thai Supreme Court Judgment which was extracted as this question.
  },
  ...
]
```

## Data size
tscc_alqac2021_law.json has 122 articles extracted from 76 sections in the Criminal Code because we inserted the original provision and all revised versions of the statement according to amending acts to the Criminal Code. 

tscc_alqac2021_question.train.json has 961 legal questions extracted from the original set of TSCC. 

## Disclaimer
Please note that TSCC dataset is created **for the academic purpose.** Therefore, please **do not** use this for commercial.

## References
\[1] KevinMercury. Thai Supreme Court Cases (TSCC) Dataset \[Online]. Available: https://github.com/KevinMercury/tscc-dataset
\[2] Nguyen Le Minh. ALQAC 2021 \[Online]. Available: https://www.jaist.ac.jp/is/labs/nguyen-lab/home/alqac-2021/
