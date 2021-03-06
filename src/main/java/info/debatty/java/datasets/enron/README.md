# ENRON dataset
The Enron Corpus is a large database of over 600,000 emails generated by 158 employees of the Enron Corporation and acquired by the Federal Energy Regulatory Commission during its investigation after the company's collapse.
https://en.wikipedia.org/wiki/Enron_Corpus

## Download
The ENRON dataset exists in multiple formats. This parser uses the version collected and prepared by the CALO Project (A Cognitive Assistant that Learns and Organizes), which can be downloaded at https://www.cs.cmu.edu/~./enron/

## Example
```java
import info.debatty.java.datasets.enron.Dataset;
import info.debatty.java.datasets.enron.Email;

public class EnronExample {

    public static void main(String[] args) throws Exception {
         Dataset enron_dataset = new Dataset(
                DBLP.class.getClassLoader().getResource("mini-enron")
                .getFile());

        for (Email email : enron_dataset) {
            // This would display the MIME text
            //System.out.println(email.getRaw());

            System.out.println(email.getUser());

            // This might be "inbox", "sent", "archive/holidays" etc.
            System.out.println(email.getMailbox());

            System.out.println(email.getSubject());
            System.out.println(email.getFrom());
            for (String address : email.getTo()) {
                System.out.println(address);
            }

            System.out.println("---");
        }
    }
}
```

Will display something like

```
badeer-r
<32086953.1075863603392.JavaMail.evans@thyme>
memo_s
Code of Ethics
office.chairman@enron.com
all.worldwide@enron.com
---
badeer-r
<12296501.1075863603653.JavaMail.evans@thyme>
memo_s
The New Power Company
office.chairman@enron.com
all.america@enron.com
---
badeer-r
<32156305.1075863603445.JavaMail.evans@thyme>
memo_s
2000 Chairman's Award
enron.announcements@enron.com
all.worldwide@enron.com
---
```