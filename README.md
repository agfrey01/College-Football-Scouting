# College-Football-Scouting
Week 1
Problem: Coaches spend too much time scouting opponents. 
Users: Coaches
Stakes: Players and coaches getting actionable insights in time for the game.
Baseline: Time to complete acceptable scouting report.
Success Metric: Report is created in less than 30 minutes with less than 3 edits.

AI Use Note
Tools and prompts: ChatGPT
What AI wrote vs what I wrote: AI wrote the prompt tempate file. I wrote the README file and ethics reflection.
Two changes after checking facts or adding context: I removed a constraint about avoiding jargon. I changed the output schema to include offense and defense assessment.


Week 2
I chose a temperature of 0.4 and a top-p of 0.9 because these settings strike a balance between consistency and natural language flow, which is ideal for drafting college football scouting reports. A temperature of 0.4 keeps the model’s output focused and factual, reducing the risk of generating speculative or irrelevant content, while still allowing enough flexibility for the text to read naturally rather than feeling overly rigid. Setting top-p at 0.9 ensures that the model primarily considers the most likely words and phrases, keeping the report coherent and structured, but still permits some variation in wording and style to avoid repetitive phrasing. Together, these settings allow the AI to produce reliable, professional, and readable scouting reports that are both accurate and engaging for the reader.

Of the three runs I did this week, I am going to carry over run 2 to Week 3. This is because it was the only successful run and because the lower temperature setting produces more consistent results.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I used AI to synthesize my thoughts and write my final paragraph.
Two changes after checking facts or adding context: None


Week 3
Few Shot prompting:
The first prompting technique I choose to was few shot prompting. Few shot prompting is a prompting technique that "provides models with a few input-output examples to induce an understanding of a given task" (SSPE p. 2). It has been shown that providing just a few high quality examples can greatly improve model performance, so I applied this to my capstone. I gave the model three examples of input statistics with the desired scouting report output format as well. I then used a prompt with just the input statistics and the model successfully replicated the scouting report format I had shown it.

Chain of Thought prompting:
The other prompting technique I tested was chain of thought prompting. It is very similar to few shot prompting, but "leverages few-shot prompting to encourage the LLM to express its thought process before delivering its final answer" (PR p. 12).  Chain of thought prompting adds a reasoning path component to the examples given to the model. This greatly improves performance for many kinds of tasks because the LLM is able to understand the reasoning behind the results given in the examples. I ran three tests of this technique for my capstone and found that Chain of Thought reasoning was incredibly successful. I used more complex input statistics that could produce incorrect results if the logical reasoning isn't understood. However using chain of thought reasoning I was able to get a correct output despite the complex data.

I chose chain-of-thought prompting because it significantly reduced latency compared to other prompting strategies. By explicitly guiding the model to reason step by step, the model produces more structured outputs in fewer tokens, which decreases the time required for generation. This approach also minimizes the need for multiple iterations or corrections, further speeding up the overall process. As a result, chain-of-thought prompting allows for faster, more efficient generation of scouting reports while maintaining clarity and accuracy, making it the ideal choice for applications where both speed and quality are important.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I conversed with ChatGPT and created the last paragraph. The first two were entirely written by me alone.
Two changes after checking facts or adding context: None


Week 5

A/B/C results:
I ran an A/B/C test comparing three different prompting strategies: plan-first, plan-and-check, and chain-of-thought. The results clearly showed that both plan-first and plan-and-check produced significantly better outputs than chain-of-thought, which tended to be less structured and more prone to small reasoning errors. Interestingly, the outputs of plan-first and plan-and-check were almost identical in quality and structure, demonstrating that the initial planning step itself provides a strong framework for generating coherent and accurate responses. The main difference between the two approaches is that plan-and-check includes an additional self-review stage, allowing the model to identify and correct potential mistakes, inconsistencies, or oversights. This extra verification step adds an important layer of reliability, especially for complex tasks such as generating detailed scouting reports. One important consideration for continuing with either plan-based approach is that the maximum token limit will need to be increased to at least 5000, to ensure that there is enough capacity for the plan, the full report, and the self-check process without truncation. Given these findings, I have decided to move forward with plan-and-check as my primary prompting strategy for my capstone project. The added risk mitigation makes it the more robust and dependable choice for high-quality outputs.


AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I conversed with ChatGPT to write the paragraph detailing the results of the A/B/C test and the Ethics/Reflection for this week.
Two changes after checking facts or adding context: Added that max tokens needed to be at least 5,000. Removed references to prompting techniques that have not been covered in this course.


Week 6

Formatting and Safety Instructions:

I chose a max_tokens setting of 2,500 after running several tests with higher limits. Initially, I set max_tokens to 50,000 to see how many tokens the model would actually use. Across five trials, it consistently used between 2,000 and 2,500 tokens, so 2,500 is sufficient to capture complete JSON outputs without truncation. This limit keeps the model efficient while ensuring full output.

Validation of the JSON outputs was handled using Python’s json library. All runs conformed to the schema defined in the prompt template, showing that structured validation effectively ensures consistent, usable data. This is essential for reducing errors in applications that rely on the output.

I continued using plan-and-check prompting, which consistently improved output accuracy and structure. While the model is more reliable than before, it is not yet fully ready for practical report generation. Iterative prompting helps maintain logical, correctly formatted outputs and reduces errors.

Latency and cost remained favorable, with responses consistently under 10 seconds and no monetary cost. This demonstrates that the approach is efficient and scalable. Going forward, I will focus on refining prompts and validation logic to further improve accuracy and produce fully dependable JSON reports.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I conversed with ChatGPT to write the paragraph detailing the results of the formatting and safety testing as well as max token testing I did this week,
Two changes after checking facts or adding context: Changed "JSONDecodeError" to "json library", JSONDecodeError is what returns the error message not what validates the json file is correct. Added context on the project and direction I plan on taking it.


Week 7

Context Block:
This week, I focused on testing the impact of contextual grounding in my prompting model by adding three markdown-based context files to the input pipeline. My goal was to determine whether structured contextual information could improve the model’s ability to generate more accurate and domain-relevant football scouting reports. I first re-ran my previous baseline test using the same configuration to establish a control. Then, I introduced the new “context pack” and temporarily removed the token cap to observe the model’s full behavior. However, the model reached the 50,000-token limit and failed to produce a response, confirming that unlimited generation can overload the model. After adjusting the limit to 25,000 tokens, I obtained my best-performing output so far—fully formatted, schema-compliant, and stylistically consistent with real scouting reports written by coaches or analysts. The added context significantly improved the factual depth, structure, and overall acceptability of the outputs. These findings demonstrate that integrating curated contextual references enhances model reliability and relevance while emphasizing the importance of token optimization to maintain efficiency.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I used ChatGPT to synthesize and edit this summary.
Two changes after checking facts or adding context: Adjusted token limit results; clarified context file purpose.

Week 9:
The sanity_check_report tool was designed to serve as a built-in reviewer that evaluates each generated scouting report for factual and logical accuracy. It checks the model’s output against trusted football data sources (like ESPN or Sports Reference) and flags inconsistencies or unsupported claims before final submission.

Adding this tool improved the reliability and professionalism of the reports — ensuring that each analysis is both data-grounded and internally consistent. The tool is being carried forward because it supports critical self-verification and aligns with coaching staff expectations for accuracy and credibility.

Guardrails to Keep:

Always validate tool input and ensure it includes the full scouting report text.

Use only trusted, publicly available reference links (never private or internal data).

Do not alter the report based on unverified or ambiguous feedback.

Final outputs must reflect both verified facts and clear reasoning.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrot
