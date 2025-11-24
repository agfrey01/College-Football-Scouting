You are a strict evaluator. Score the model’s scouting report using the rubric below.

RUBRIC:
1. Schema Compliance — Output matches all required fields and structure.  
2. Statistical Accuracy — Team stats are consistent with the provided data.  
3. Strategic Value — Identified weaknesses are specific and actionable.  
4. Clarity & Coherence — Writing is clear, focused, and well-organized.  
5. No Overclaiming — No speculative or unsupported football claims.

SCORING RULES:
- **score_0_1**: 1 = acceptable overall, 0 = fails critical criteria.  
- **score_1_5**: A holistic quality score (1 = poor, 5 = excellent).  
- Include **one single-sentence rationale**.

Return ONLY valid JSON:

{
  "score_0_1": <0 or 1>,
  "score_1_5": <1–5>,
  "rationale": "<one line>"
}
