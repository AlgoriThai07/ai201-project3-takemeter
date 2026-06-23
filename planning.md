Community: I choose the soccer community and more specially the FIFA World cup 2026 community. This is a good community for a classification task because it is a community of passionate fans who are very engaged in the topic. The discourse is varied enough to be interesting because there are many different opinions and perspectives on the topic. For example, there are fans who are very passionate about their team, fans who are very passionate about the game itself, and fans who are very passionate about the topic of sportsmanship. 

Labels: 
The 4 labels are:
- Analysis: Captures tactical/stat-based threads or thoughtful replies
Example: 
+ Pochettino’s USMNT seems to be forming a press-first identity. The team looks more comfortable forcing turnovers high than controlling long possession spells.
+ Portugal’s midfield has technical quality, but Bruno, Vitinha, and Neves may struggle in recovery runs if the fullbacks push high
- Hot-take: Opinionated but not abusive, clearly not objective
Example: 
+ Why Christian Pulisic is actually the most overrated player on the USMNT
+ England's so-called "golden generation" was a complete failure
- Reaction: Immediate emotional responses, short replies to live action
Example: 
+ Ooooooooooh my what a goal! Japan 2-0!
+ How on earth did he miss that?!??
- Updates: match score, results, live updates
Example: 
+ Mo Salah wins the Player of the Match award at a World Cup match for the first time in his career
+ Egypt beat New Zealand 3-1 and get their first-ever win at the World Cup


Hard edge cases: The post that use cherry picking logic to support their opinion, which can be see as hot-take or analytics.

Example: 
+ Luka Modric is not a great World Cup player because he only scored 2 goals in 18 games. This is a good example of cherry picking because it ignores the fact that Modric is a midfielder and not a striker, and that he is known for his playmaking ability. The one-stat post above is borderline; the framing is accusatory and the stat is selected for effect rather than as part of an argument -> hot-take.


Data collection plan: I will collect the examples on X by searching for the FIFA World cup 2026 hashtag and sorting by "latest". I will collect around 50 examples per label, for a total of 200 examples. If a label is underrepresented after 50 examples, I will increase the number of examples I collect per label. 

Evaluation metrics: 
- Accuracy: measures the overall correctness of the model
- Macro F1-score: measures the harmonic mean of precision and recall across all labels, giving equal weight to each label. This is important because some labels may be more common than others, and we want to ensure that the model is performing well on all labels.
- Precision per label: Tells how many of the model's predictions for a specific label were correct
- Recall per label: Tells how many actual instances of a specific label the model correctly identified
- F1-score per label: The harmonic mean of precision and recall for each label
- Confusion Matrix: Visualizes the performance of the model, showing the number of correct and incorrect predictions for each label

Definition of success: 
I would consider it successful if it performs clearly better than the zero-shot Groq baseline and shows balanced performance across all 4 labels. 
A strong result would be around 75-80% overall accuracy with a macro F1-score of 0.70 or higher, indicating that the model is performing well on all labels. 

My minimum deployment standard would be:
- Macro F1: >= 0.75
- F1-score per label: >= 0.65 for every label
- Precision of at least 0.8 for analysis, so the model doesn't over-label weak or cherry-picked arguments as high-quality analysis
- A confusion matrix showing that most errors occur between understandable neighboring categories like hot take and reaction, rather than unrelated labels.

AI Tool Plan:
- Label stress-testing: Use ChatGPT to generate 5-10 examples for each label, and see if the model can classify them correctly. 
- Annotation assistance: Use ChatGPT to pre-label a batch of examples before reviewing them myself. I will label 5 examples per label using ChatGPT, and if the model is accurate, I will use it to label the rest of the examples. 
- Failure analysis: Use ChatGPT to analyze the list of wrong predictions and identify patterns. I will look for patterns in the types of posts that the model misclassifies, and I will use this information to improve the model.

## AI Usage for Annotation

I used an LLM to pre-label examples using my four label definitions: `analysis`, `hot_take`, `reaction`, and `updates`. I then manually reviewed every example and corrected labels when needed. The AI helped speed up the first pass, but I made the final annotation decisions, especially for ambiguous cases.

## Difficult Labeling Examples

### 1. Cherry-picked statistic or narrative

**Example:** “Argentina only wins because of Messi. Team is average.”

**Possible labels:** `analysis`, `hot_take`  
**Final label:** `hot_take`

**Reason:** The post makes a broad claim without balanced evidence. It focuses only on Messi and ignores Argentina’s squad, tactics, and team structure.

### 2. Emotional reaction mixed with judgment

**Example:** “VAR saved them there. Controversial but correct?”

**Possible labels:** `reaction`, `hot_take`  
**Final label:** `reaction`

**Reason:** The post reacts to a specific match moment. It includes judgment, but it does not make a broader unsupported claim.

### 3. Factual result with implied interpretation

**Example:** “Spain high possession leads to victory.”

**Possible labels:** `updates`, `analysis`  
**Final label:** `updates`

**Reason:** The post reports a match outcome with a performance detail, but it does not explain the tactical reason behind the result.

