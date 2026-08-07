---
title: "Converting HUST Credits to ECTS"
date: 2026-08-07
permalink: /notes/ects-credit-conversion/
categories:
  - notes
tags:
  - HUST
  - ECTS
  - higher education
excerpt: "A workload-based HUST credit conversion with course-level detail and country-specific ECTS estimates."
---

This page converts my HUST Talent Program in Mathematics and Informatics (K62) transcript into workload-based ECTS estimates. It gives admissions reviewers the hours behind the HUST credits; it does not replace an evaluation by the receiving university. The official [K62 Talent Program curriculum](https://fami.hust.edu.vn/ctdt-tai-nang-toan-tin-cho-cac-khoa-tu-k62/) is published by HUST's Faculty of Mathematics and Informatics.

The HUST conversion guidance is in [1] and [2], and the K62 curriculum is in [3].

For course descriptions, use HUST FaMI's [English course-outline catalog](https://fami.hust.edu.vn/en/management-information-system-course-outlines/), [Mathematics–Informatics course summaries](https://fami.hust.edu.vn/tomtathocphancntoantin/), and [engineering Mathematics–Informatics course summaries](https://fami.hust.edu.vn/motahocphan_ks_toantin/). These are source catalogs, not a claim that every course has a current public PDF.

## Baseline calculation

I use the detailed course workload, not a direct multiplication of 132 TC by a single constant.

- **1 HUST training credit (TC)** represents approximately **50 standardized study hours** [1], [2].
- A course structure written as A(B-C-D-E) records the module credit, lecture periods, exercise/discussion periods, laboratory/practice periods, and self-study hours.
- The main result on this page uses 30 hours per ECTS, as in the HUST conversion documents.

For a course, the workload is:

$$
\text{Hours} = \left(15B + 30\left(\frac{C}{2}+\frac{D}{2}\right)\right)\frac{50}{60} + 15E.
$$

The ECTS estimate is then:

$$
\text{ECTS} = \frac{\text{total study hours}}{30}.
$$

The formula assumes a 15-week term and 50-minute teaching periods.

### Example: Probability Theory

MI3350, Probability Theory, has structure 3(3-1-0-6).

| Step | Calculation | Result |
| --- | --- | ---: |
| Classroom periods | \\(3\\times15+(1/2)\\times30\\) | 60 periods |
| Classroom workload | \\(60\\times50/60\\) | 50 hours |
| Self-study | \\(6\\times15\\) | 90 hours |
| Total | \\(50+90\\) | 140 hours |
| ECTS at 30 hours | \\(140/30\\) | 4.67 |

## Totals

The detailed table below gives:

- **132 HUST credits**;
- **6,192.5 total study hours**;
- **206.45 ECTS**, when the rounded course-level ECTS values are summed.

Using the total hours directly gives \\(6{,}192.5/30=206.42\\) ECTS. The 0.03 difference comes from summing rounded course values. The workbook also contains a summary cell with 205.65 ECTS; it does not match the detailed table, so I do not use it.

## Country and system conventions

I keep one course table and change only the conversion rule. The figures below are workload estimates from 6,192.5 hours, not an admission decision. Use the rule published by the target university or country, and send the HUST documents with the application.

| Destination | Published convention | Workload estimate from this transcript | Official source |
| --- | --- | ---: | --- |
| Netherlands | 1 ECTS = 28 hours | 221.16 ECTS | [Government.nl](https://www.government.nl/themes/education/secondary-vocational-education-mbo-and-tertiary-higher-education/tertiary-higher-education) |
| Italy | 1 CFU = 1 ECTS = 25 hours | 247.70 ECTS | [Italian Ministry of University and Research](https://www.mur.gov.it/it/urp/urp-orienta) |
| Spain | 1 ECTS = 25–30 hours | 206.42–247.70 ECTS | [Official State Gazette](https://www.boe.es/buscar/act.php?id=BOE-A-2003-17643) |
| Poland | 1 ECTS = 25–30 hours | 206.42–247.70 ECTS | [Polish higher-education law](https://www.gov.pl/attachment/d6975935-4b24-4be3-96f1-09c51589958a) |
| Turkey | 1 ECTS = 25–30 hours | 206.42–247.70 ECTS | [Council of Higher Education](https://uluslararasi.yok.gov.tr/en/page/517) |
| Germany | HUST exchange guidance uses 1 ECTS = 30 hours; DAAD gives a general 25–30-hour range | 206.42 ECTS | [HUST guidance](https://ctt.hust.edu.vn/Upload/Nguyen%20Quoc%20Dat/files/DTDH_bieumau/Hoc_tap/Qui%20%C4%91%E1%BB%95i%20t%C3%ADn%20ch%E1%BB%89%20VN%20sang%20ECTS_%20Eng.pdf) · [DAAD National Agency](https://eu.daad.de/programme-und-hochschulpolitik/der-bologna-prozess/themen-im-bologna-prozess/studienstruktur-qualifikationsrahmen-ects/) |
| United Kingdom | 1 UK credit = 10 notional hours; this is not ECTS | 619.25 UK credits | [GOV.UK](https://www.gov.uk/student-finance-on-or-after-1-january-2027/eligibility) |
| United States | Credit hours are institutionally defined; no national ECTS ratio | No automatic conversion | [U.S. Department of Education](https://fsapartners.ed.gov/knowledge-center/library/dear-colleague-letters/2011-03-18/gen-11-06-subject-guidance-to-institutions-and-accrediting-agencies-regarding-credit-hour-defined-final-regulations-published-october-29-2010) |

For ECTS countries, the European framework is 60 ECTS for a full-time academic year, while the hours attached to one ECTS credit can vary nationally between 25 and 30 [4], [5]. The country rows above are useful for a first-pass estimate; the programme's admissions office still decides what it accepts.

## Full course-by-course conversion

Hours are total workload. ECTS values are rounded to two decimal places for each course.

| Course (English) | Code | HUST TC | Structure | Hours | Related field | ECTS |
| --- | --- | ---: | --- | ---: | --- | ---: |
| Fund. Principles of Marxism-Leninism II | SSH1120 | 3 | 3(3-0-0-6) | 127.5 | General Education | 4.25 |
| Revolution Policy of VCP | SSH1130 | 3 | 3(3-0-0-6) | 127.5 | General Education | 4.25 |
| Ho Chi Minh Ideology | SSH1050 | 2 | 2(2-0-0-4) | 85 | General Education | 2.83 |
| Intro. to the Legal Environment | EM1170 | 2 | 2(2-0-0-4) | 85 | General Education | 2.83 |
| Calculus I | MI1111 | 4 | 4(3-2-0-8) | 182.5 | Mathematics | 6.08 |
| Calculus II | MI1121 | 3 | 3(2-2-0-6) | 140 | Mathematics | 4.67 |
| Calculus III | MI1131 | 3 | 3(2-2-0-6) | 140 | Mathematics | 4.67 |
| Algebra | MI1141 | 4 | 4(3-2-0-8) | 182.5 | Mathematics | 6.08 |
| Physics I | PH1110 | 3 | 3(2-1-1-6) | 140 | Physics | 4.67 |
| Physics II | PH1120 | 3 | 3(2-1-1-6) | 140 | Physics | 4.67 |
| Introduction to Management | EM1010 | 2 | 2(2-0-0-4) | 85 | Management | 2.83 |
| Introduction to Informatics | IT1110 | 4 | 4(3-1-1-8) | 182.5 | Computer Science | 6.08 |
| Modern Algebra | MI2053 | 3 | 3(3-0-0-6) | 127.5 | Mathematics | 4.25 |
| Functional Analysis | MI2063 | 4 | 4(4-1-0-8) | 182.5 | Mathematics | 6.08 |
| Discrete Mathematics | MI3010 | 3 | 3(3-1-0-6) | 140 | Mathematics / Computer Science | 4.67 |
| Numerical Analysis | MI3040 | 4 | 4(4-1-0-8) | 182.5 | Mathematics / Computer Science | 6.08 |
| Intro. to Mathematics and Informatics | MI2000 | 3 | 3(2-0-2-6) | 140 | Mathematics / Computer Science | 4.67 |
| Complex Analysis and Applications | MI3080 | 3 | 3(3-1-0-6) | 140 | Mathematics | 4.67 |
| Programming Techniques | MI3310 | 2 | 2(2-0-1-4) | 97.5 | Computer Science | 3.25 |
| Probability Theory | MI3350 | 3 | 3(3-1-0-6) | 140 | Mathematics | 4.67 |
| Operating Systems | MI3370 | 2 | 2(2-1-0-4) | 97.5 | Computer Science | 3.25 |
| LIFE 1 | FL1106 | 0 | 0 | 0 | Language | 0 |
| LIFE 2 | FL1107 | 0 | 0 | 0 | Language | 0 |
| LIFE 3 | FL1108 | 3 | 3(0-6-0-6) | 165 | Language | 5.50 |
| LIFE 4 | FL1109 | 3 | 3(0-6-0-6) | 165 | Language | 5.50 |
| Object-Oriented Programming | MI3323 | 2 | 2(2-1-0-4) | 97.5 | Computer Science | 3.25 |
| Data Structures and Algorithms | MI3060 | 3 | 3(3-1-0-6) | 140 | Computer Science | 4.67 |
| Mathematical Statistics | MI3360 | 2 | 2(2-1-0-4) | 97.5 | Mathematics | 3.25 |
| Optimization Methods | MI3050 | 4 | 4(4-1-0-8) | 182.5 | Mathematics | 6.08 |
| Database | MI3090 | 3 | 3(3-1-0-6) | 140 | Computer Science | 4.67 |
| Stochastic Models and Applications | MI5040 | 3 | 3(3-1-0-6) | 140 | Mathematics | 4.67 |
| Computer Systems and Networks | MI4060 | 3 | 3(2-1-1-6) | 140 | Computer Science | 4.67 |
| Partial Differential Equations | MI3073 | 4 | 4(4-1-0-8) | 182.5 | Mathematics | 6.08 |
| System Analysis and Design | MI3120 | 3 | 3(3-1-0-6) | 140 | Computer Science | 4.67 |
| Project I | MI3380 | 3 | 3(0-0-6-6) | 165 | Mathematics / Computer Science | 5.50 |
| Project II | MI3390 | 3 | 3(0-0-6-6) | 165 | Mathematics / Computer Science | 5.50 |
| Technical Writing and Presentation | MI2030 | 3 | 3(2-2-0-6) | 140 | Communication | 4.67 |
| Computer Architectures | MI4342 | 3 | 3(3-1-0-6) | 140 | Computer Science | 4.67 |
| Computation Programming | MI4160 | 3 | 3(3-1-0-6) | 140 | Mathematics / Computer Science | 4.67 |
| Decision Support System | MI4210 | 3 | 3(3-1-0-6) | 140 | Computer Science | 4.67 |
| Data Analysis | MI4020 | 3 | 3(3-1-0-6) | 140 | Mathematics / Computer Science | 4.67 |
| Combinatorial Optimization I | MI4311 | 3 | 3(3-1-0-6) | 140 | Mathematics | 4.67 |
| Philosophy of Marxism and Leninism | SSH1111 | 3 | 3(3-0-0-6) | 127.5 | General Education | 4.25 |
| Bachelor of Science Research Project | MI4902 | 8 | 8(0-0-16-16) | 440 | Mathematics / Computer Science | 14.67 |
| **TOTAL** |  | **132** |  | **6,192.5** |  | **206.45** |

The field labels are descriptive only. A course can appear in more than one field, so these totals must not be added together:

| Related field | HUST credits | ECTS from course-level values |
| --- | ---: | ---: |
| Mathematics | 73 | 116.35 |
| Computer Science | 58 | 94.28 |
| Physics | 6 | 9.34 |
| Management | 2 | 2.83 |
| Language | 6 | 11.00 |
| Communication | 3 | 4.67 |
| General Education | 13 | 18.41 |

For example, Numerical Analysis appears under mathematics, computer science/software engineering, and signal processing.

## Suggested wording for an application

> HUST Bachelor in Mathematics and Informatics: 132 HUST credits and 6,192.5 documented study hours. Using the HUST 30-hours-per-ECTS convention, this corresponds to approximately 206 ECTS. Supporting course-level workload and conversion documents are available on request.

## References

[1] Hanoi University of Science and Technology, “Credit conversion guidance,” Decision No. 374/HD-ĐHBK-ĐT, 2022. [Online]. Available: [HUST PDF](https://ctt.hust.edu.vn/Upload/Nguyen%20Quoc%20Dat/files/DTDH_bieumau/Hoc_tap/Qui%20%C4%91%E1%BB%95i%20t%C3%ADn%20ch%E1%BB%89%20VN%20sang%20ECTS_%20Eng.pdf). [Accessed: Aug. 7, 2026].

[2] Hanoi University of Science and Technology, “Credit conversion guidance,” Decision No. 7323/HD-ĐHBK-ĐT, 2023. [Online]. Available: [HUST PDF](https://ctt.hust.edu.vn/Upload/Nguyen%20Quoc%20Dat/files/DTDH_QDQC/Hoctap/QD7323DT2023.pdf). [Accessed: Aug. 7, 2026].

[3] Hanoi University of Science and Technology, “Talent Program in Mathematics and Informatics curriculum, cohort K62,” Faculty of Applied Mathematics and Informatics. [Online]. Available: [HUST curriculum](https://fami.hust.edu.vn/ctdt-tai-nang-toan-tin-cho-cac-khoa-tu-k62/). [Accessed: Aug. 7, 2026].

[4] European Commission, “European Credit Transfer and Accumulation System (ECTS),” *Education and Training*. [Online]. Available: [ECTS overview](https://education.ec.europa.eu/education-levels/higher-education/inclusive-and-connected-higher-education/european-credit-transfer-and-accumulation-system). [Accessed: Aug. 7, 2026].

[5] European Commission, *ECTS Users' Guide 2015*. [Online]. Available: [EU publication](https://op.europa.eu/publication/doi/10.2766/87592). [Accessed: Aug. 7, 2026].

[6] Government of the Netherlands, “Tertiary (higher) education.” [Online]. Available: [source](https://www.government.nl/themes/education/secondary-vocational-education-mbo-and-tertiary-higher-education/tertiary-higher-education). [Accessed: Aug. 7, 2026].

[7] Italian Ministry of University and Research, “Crediti formativi universitari.” [Online]. Available: [source](https://www.mur.gov.it/it/urp/urp-orienta). [Accessed: Aug. 7, 2026].

[8] Spain, *Real Decreto 1125/2003*. [Online]. Available: [source](https://www.boe.es/buscar/act.php?id=BOE-A-2003-17643). [Accessed: Aug. 7, 2026].

[9] Republic of Poland, *Law on Higher Education and Science*. [Online]. Available: [source](https://www.gov.pl/attachment/d6975935-4b24-4be3-96f1-09c51589958a). [Accessed: Aug. 7, 2026].

[10] Republic of Türkiye, Council of Higher Education, “ECTS and student workload.” [Online]. Available: [source](https://uluslararasi.yok.gov.tr/en/page/517). [Accessed: Aug. 7, 2026].

[11] GOV.UK, “Student finance: eligibility.” [Online]. Available: [source](https://www.gov.uk/student-finance-on-or-after-1-january-2027/eligibility). [Accessed: Aug. 7, 2026].

[12] U.S. Department of Education, “Definition of a credit hour.” [Online]. Available: [source](https://fsapartners.ed.gov/knowledge-center/library/dear-colleague-letters/2011-03-18/gen-11-06-subject-guidance-to-institutions-and-accrediting-agencies-regarding-credit-hour-defined-final-regulations-published-october-29-2010). [Accessed: Aug. 7, 2026].

[13] DAAD National Agency for Erasmus+ Higher Education Cooperation, “Study structure, qualifications framework and ECTS.” [Online]. Available: [source](https://eu.daad.de/programme-und-hochschulpolitik/der-bologna-prozess/themen-im-bologna-prozess/studienstruktur-qualifikationsrahmen-ects/). [Accessed: Aug. 7, 2026].
