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
What AI wrote vs what I wrote: 

Week 10:
This week I added a safety - refusal block to my prompt template to ensure no malicious inputs can be used on my model as well as preventing the model from unethical behavior. I had limited success implementing my new block and had only a 60% success rate when tested against my attack set. I did however iterate after each attempt and the last three attack tests I ran were successful. After running my attack tests and optimziing the safety - refusal block I ran three successful friction tests with normal inputs. Because of the success after iterating on the safety - refusal block I will keep this going forward. With the current high profile investigations into illegal scouting practices in gambling, I believe it is of the utomost importance to prevent my model from being used in any unethical way. This week I also adjusted my prompt template to make it more concise and clear. The outputs from the model continue to improve with each iteration on this project and I believe that I will be able to meet my success criteria by the project deadline.


AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: I used ChatGPT to create my attack set and help write my safety-refusal block.
Two changes after checking facts or adding context: Adjusted team name to be real team names not attack type. Added context on privacy and PII regulations to help create safety-refusal block.

Week 11: 
Optimization Block
Goals: To create a concise scouting report for a football team with minimal inputs from the user that is informative to a football fan, coach, player, or media member.
Constraints: The output must fit onto one page, be know more than 500 words, and be formatted correctly as a json file. The model must take no longer than 10 minutes to return the  report. The API being used for this project only allows 30,000 tokens per input. The model may only use the user inputted data (if in compliance with safety block) and publically available external data to generate a response. 
Quality Floor: The report has no inaccurate statistics, makes no unstubstaniated claims, and produces actionable insights. 
Target Latency: Under 10 minutes
Budget USD: 0

After performing a parameter sweep of my current model I have conclude that the only parameter I intended to change is temperature. I tested a change to top-p, lowering it from 0.9 to 0.5 but the increase in latency was drastic. That test wsa the slowest test I have had to date (~38 seconds) and was over double the second longest (~18 seconds). Both of these latency times are well below my goal of under my constraint of returning an output in under 10 minutes, but since I noticed no associated increase in quality I will keep top-p consistent with my previous test. Max tokens will also remain consistent. My API only allows 30,000 tokens per input and currently my max tokens is set at 25,000, so I cannot raise it enough to significantly impact the outputs. I tested lowering it with a slightly decrease in latency occuring, but there was also an associated slight decrease in quality. Because quality is my highest concern and latency is still well below my goal I will keep max tokens at 25,000 going forward. I tested multiple new temperature settings including 0.6, 0.7, and 0.8. These new temperatures made the output more creative and allowed the model to be more eloquent in its analysis of the data. There was little effect to speed when temperature was changed and quality also remained consistent if not slightly improved. Because of this I will update my temperature setting to 0.8 going forward. I believe a more creative eloquent output is preferable to a more deterministic one because we are asking the model to make inferences and creativity will lead to better inferences. To summarize my parameters after the sweep are going to be temperature = 0.8, top-p = 0.9, and max tokens = 25,000.

AI Use Note
Tools and prompts/settings: None
What AI wrote vs what I wrote: I did not use any AI to help with this week's assignments.
Two changes after checking facts or adding context: N/A

Week 12:
After testing the regression set on my model, I computed a 90% pass rate. 9 out of the 10 tests were successful with most also getting a score of a 4 or a 5. This indicates my model is relatively stable with minor edge case issues. The definition of done threshold for the regression set will be set at 90% for next week with no tests having a critical failure. This crossing this threshold will give me confidence that my model is ready for use by others. Edge cases continue to be a problem, particularly when the case involves an error in the inputted URL. To fix this in Week 13 I plan on updating my safety block to have stronger protocols in place for identifying faulty URLs and rejecting the input. 

AI Use Note
Tools and prompts/settings: None
What AI wrote vs what I wrote: I did not use any AI to help with this week's assignments.
Two changes after checking facts or adding context: N/A

Week 13:
This week I experimented with expanding the model’s context by adding a large statistical file (stats2024.csv) directly into the prompt. The goal was to improve scouting report accuracy by giving the model access to more detailed numeric data during inference. I updated the notebook to load and inject the full CSV content into the API call, alongside the prompt template, tools, and regression set.

However, after running the updated workflow, the request consistently exceeded the token limit allowed by the API. As a result, the model returned no usable output, preventing any meaningful regression or A/B evaluation. Because this change significantly increases prompt size and makes the system unstable, I will not be keeping this modification going forward.

Next week, I will revert to a lighter-weight context approach and explore alternative methods such as preprocessing the stats into summarized features or storing structured data in smaller chunks that can be selectively loaded based on team. This will maintain performance while avoiding token overflows.

AI Use Note
Tools and prompts/settings: ChatGPT
What AI wrote vs what I wrote: ChatGPT editted my writing and formatted into a cohesive narrative for both my README.md file and CHANGELOG.md file
Two changes after checking facts or adding context: I had to remove the extraneous details the model added to my writing. I also had to add more detail afterward to comprehensively update my README.md file.
