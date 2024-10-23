# Mental healt chatbot
This was meant to be a multilingual mental health chatbot. However, the part that worked well is in English. Due to time constraints and overly ambitious initial plans, it became more of a mental health IR system. In this repository, you can find the code for the baseline model.

We use *Llama-2–7b-chat-hf* (Meta, 2024), which has 7 billion parameters and is pre-trained on multilinugal data.

We used this dataset: https://www.kaggle.com/datasets/narendrageek/mental-health-faq-for-chatbot for fine-tuning. Aside form this, we used a machine translated version to Swedish, to try to make the model response in Swedish. While this worked, it was obviously not ideal.

This project has two main drawbacks:
- The size and quality of data
    The dataset was very small (only 98 unique lines, which was split between fine-tuning and validation sets) and sometimes not of great quality. For this reason, it seems the model never generalized the information, but retrieved the most relevant response. Hence, being an IR system rahter than a chatbot which was our intended goal.
- The size of the Llama model
    It is possible Llama was not the best fit for this project. It is a very large model which caused a lot of computational issues given our resources. A better choice might have been using Bart. I did work on getting Bart to work and got relatively far (to the point where it generated nonsensical responses), but we managed to get further with Llama before I could finish the Bart implementation. And because we had limited time, this was the approach we chose. 

Some positive things were that:
- We managed to make it "chatty", meaning while it mostly retrieved data from the dataset, it also added comments like "Sure, I'd be happy to help! There are several ways to find a support group for mental health".
- It has good potential to be a good and accurate chatbot, with better data.
- It did produce responses in both English and Swedish, although not always.

### Example results
Here is one example of a question and response given by the chatbot:

#### English
>Q: Var kan jag hitta en stödgrupp?
>A: Var kan jag hitta en stödgrupp? [/INST] Sure, I'd be happy to help! There are several ways to find a support group for mental health. Here are a few options you might consider:
>1. National Alliance on Mental Illness (NAMI): NAMI is a non-profit organization that provides education, support, and advocacy for people affected by mental illness. They have local chapters across the United States, which offer support groups for individuals and their families. You can find your local NAMI chapter by visiting their website or calling their national helpline at 1-800-950-6264.
>2. Mental Health America: Mental Health America is a national organization that provides information and resources for people struggling with mental health conditions. They have a database of local support groups and hotlines, as well as online support groups. You can visit their website at mentalhealthamerica.net or call their national helpline at 1-800-950-6264.
>3. Psychology Today: Psychology Today is a website that provides a directory of mental health professionals, including therapists and support groups. You can search for support groups in your area by using their online directory.
>4. Your healthcare provider: Your healthcare provider may be able to refer you to a support group or provide information about local resources.
Remember, it's important to take care of your mental health and seek support when you need it. These support groups can provide a safe and confidential space to share your experiences and connect with others who are going through similar challenges.

#### Swedish
>Q: Var kan jag hitta en stödgrupp?
>A:  Du kan hitta en stödgrupp genom att kontakta en av följande organisationer:
>* Självhjälpsrörelsen (Sverige)
>* Riksorganisationen för psykisk hälsa (ROP)
>* Psykiatriska sällskapet (PS)
>* Sällskapet för psykisk hälsa (SP)
>* Stiftelsen för psykisk hälsa (SPH)
>Dessa organisationer erbjuder stödgrupper för människor med olika psykiska problem, däribland depression, ångest, bipolär sjukdom, ADHD, personliga problem och mer. Stödgrupperna leds av välutbildade ledare och är anonyma, vilket innebär att deltagarna inte behöver vara ensamma med sina problem.
>Du kan också hitta en stödgrupp på internet. Det finns många webbplatser och forum där du kan hitta information och stöd.
>Om du vill hitta en stödgrupp i din region, kan du kontakta din läkare, en psykolog eller en socialtjänst. De kan hjälpa dig att hitta en grupp som passar din behov.
