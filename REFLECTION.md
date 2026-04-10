# Reflection -- Hello, Azure AI

Answer these questions after completing the activity (2-3 sentences each). Connect your answers to specific things you observed while coding and experimenting.

## 1. Service Surprises

Which of the three Azure AI services (OpenAI, Content Safety, Language) surprised you the most? Connect this to something specific you observed during your experiments -- a response you didn't expect, a behavior that seemed too easy or too hard, or a result that made you rethink how the service works.

I was impressed with the reasoning/logic displayed in some of the responses.  Not only was a complaint categorized correctly, but the reasoning was able to pull out the primary complaint or issue when there was more than one complaint being made, like the prompt below in question 3.  If the complaint was mostly straightforward, the confidence score was 90 or above just about every time.  The only way I could force the confidence score down was to combine unrelated complaints (there is trash on my street and there's a pothole on Poplar and my neighbors are noisy).  In those cases, the confidence score fell around 60-70 because there was no clear primary complaint.

## 2. Lazy Initialization

How would you explain the lazy initialization pattern to a colleague? Why is it used instead of creating clients at the top of the file?

Since we're using paid-for services, it makes sense to use lazy initialization because it will delay the use of these services until the first time it's needed.  Instead of creating objects when the script is started, you make them just before you need it, if you need it at all.  It can also reduce start time for your program/application, since you're not initializing everything at the beginning

## 3. Content Safety in the Real World

A resident files this complaint: *"A man was assaulted at this intersection because the street light has been out for months."* This text describes real violence but is a legitimate safety concern. Should the system block it, flag it for human review, or pass it through? What factors would you weigh in making that decision?

It seems that any mention of violence will flag the item, even though it shouldn't be blocked.  This complaint was flagged, and I entered my own prompt about seeing a dog hit by a car, which also got flagged.  If I were implementing this system, I wouldn't block anything outright until the tool had been tested and run through lots of real-world complaints, to avoid blocking something that needs immediate attentions.  I'd want human review for anything that gets flagged so that the tool can be fine-tuned and then switched to blocking high-confidence abuse submissions.