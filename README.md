
import Java.util.*; 
import edu.stanford.nlp.pipeline.*;
import edu.stanford.nlp.ling.*; 
import edu.stanford.nlp.ling.CoreAnnotations.*;  

public class example
{
    public static void main(String[] args)
    {
        Properties props = new Properties(); 
        props.put("annotators", "tokenize, ssplit, pos, lemma"); 
        pipeline = new StanfordCoreNLP(props, false);
        String text = /* the string you want */; 
        Annotation document = pipeline.process(text);  

        for(CoreMap sentence: document.get(SentencesAnnotation.class))
        {    
            for(CoreLabel token: sentence.get(TokensAnnotation.class))
            {       
                String Word = token.get(TextAnnotation.class);      
                String lemma = token.get(LemmaAnnotation.class); 
                System.out.println("lemmatized version :" + lemma);
            }
        }
    }
}
