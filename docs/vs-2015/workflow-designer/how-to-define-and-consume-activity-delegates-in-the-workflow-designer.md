---
title: 'Nasıl yapılır: İş Akışı Tasarımcısı etkinlik temsilcilerini tanımlama ve kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603850"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma
[!INCLUDE[net_v45](../includes/net-v45-md.md)] etkinlik için yeni bir kullanıma hazır tasarımcı içerir <xref:System.Activities.Statements.InvokeDelegate> . Bu tasarımcı, veya gibi öğesinden türetilen etkinliğe temsilciler atamak için kullanılabilir <xref:System.Activities.ActivityDelegate> <xref:System.Activities.ActivityAction> <xref:System.Activities.ActivityFunc%601> .

### <a name="define-an-activity-delegate"></a>Etkinlik temsilcisi tanımlama

1. İçinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Dosya**, **Yeni**, **Proje**' yi seçin. Sol taraftaki **Iş akışı** düğümünü ve sağ taraftaki **Iş akışı konsol uygulaması** şablonunu seçin. Projeyi (isterseniz) adlandırın ve **Tamam**' a tıklayın.

2. **Çözüm Gezgini** projeye sağ tıklayın ve **Ekle**, **Yeni öğe..**. seçeneğini belirleyin. Sol taraftaki **Iş akışı** düğümünü ve sağdaki **etkinlik** şablonunu seçin. Yeni etkinliği **MyForEach. xaml** olarak adlandırın ve **Tamam**' a tıklayın. Etkinlik iş akışı Tasarımcısı 'nda açılır.

3. İş akışı tasarımcısında, **bağımsız değişkenler** sekmesine tıklayın.

4. **Bağımsız değişken Oluştur**' a tıklayın. Yeni bağımsız değişken **öğelerini**adlandırın.

5. **Bağımsız değişken türü** sütununda, **[T] dizisini**seçin.

6. Tür tarayıcısında  **nesne**' yi seçin. **Tamam**’a tıklayın.

7. **Bağımsız değişken Oluştur** ' a tekrar tıklayın. Yeni bağımsız değişken **gövdesini**adlandırın. Yeni bağımsız değişkenin **Yön** sütununda **özellik**' i seçin.

8. Bağımsız değişken türü sütununda **türler Için Araştır ' ı seçin...**

9. Tür tarayıcısında, **tür adı** alanına **ActivityAction** girin. Ağaç **görünümünde \<T> ActivityAction** öğesini seçin. **ActivityAction \<Object> ** türünün bağımsız değişkenine atanması için görüntülenen açılan menüden **nesne** ' yi seçin.

10. <xref:System.Activities.Statements.While>Araç kutusunun **Denetim akışı** bölümünden bir etkinliği tasarımcı yüzeyine sürükleyin.

11. Etkinliği seçin <xref:System.Activities.Statements.While> ve **değişkenler** sekmesini seçin.

12. **Değişken Oluştur**' u seçin. Yeni değişken **dizinini**adlandırın.

13. **Değişken türü** sütununda **Int32**' yi seçin. **Kapsamı** **sırasında**ve **varsayılan** sütunu boş bırakın.

14. Etkinliğin **Condition** özelliğini <xref:System.Activities.Statements.While> **< Items. length; dizinine**göre ayarlayın.

15. <xref:System.Activities.Statements.InvokeDelegate>Araç kutusu ' ndan bir **Primitives** etkinliği etkinliğin **gövdesine** sürükleyin <xref:System.Activities.Statements.While> .

16. Temsilci açılan kutusunda **gövde** ' yi seçin.

17. Etkinliğin **Özellikler** kılavuzunda <xref:System.Activities.Statements.InvokeDelegate> **..** . öğesine tıklayın. düğmesine basın. **Delegate Arguments**

18. **Bağımsız değişkenin adlandırılmış bağımsız**değişkeninin **değer** sütununda, **[Dizin] öğesini**girin. **Temsilci bağımsız değişkenleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

19. Etkinliği <xref:System.Activities.Statements.Assign> etkinliğin altındaki yatay çizgiye sürükleyin <xref:System.Activities.Statements.InvokeDelegate> . <xref:System.Activities.Statements.Assign>Etkinlik oluşturulur ve <xref:System.Activities.Statements.Sequence> **MyForEach** etkinliğinin **gövde** bölümündeki iki etkinliği içerecek şekilde otomatik olarak bir etkinlik oluşturulur. **Body** bölümü yalnızca tek bir etkinlik içerebileceğinden, bu sıra gereklidir. Otomatik olarak yeni bir <xref:System.Activities.Statements.Sequence> etkinlik oluşturulması yeni bir özelliğidir [!INCLUDE[net_v45](../includes/net-v45-md.md)] .

20. Etkinliğin **to** özelliğini <xref:System.Activities.Statements.Assign> **index**olarak ayarlayın. **Assign** etkinliğinin **Value** özelliğini **index + 1**olarak ayarlayın.

    Özel **MyForEach** etkinliği artık **öğe** koleksiyonu aracılığıyla kendisine geçirilen her bir değer için bir kez rastgele bir etkinlik çağırır. Bu, koleksiyondaki değerler etkinliğin girdileri olarak oluşturulur.

### <a name="use-the-custom-activity-in-a-workflow"></a>Bir iş akışında özel etkinliği kullanma

1. **CTRL + SHIFT + B**tuşlarına basarak projeyi derleyin.

2. **Çözüm Gezgini**, tasarımcıda **Workflow1. xaml** ' yi açın.

3. Araç kutusundan bir **MyForEach** etkinliğini tasarımcı yüzeyine sürükleyin. Etkinlik, araç kutusunun bir bölümünde proje ile aynı ada sahip olacaktır.

4. **MyForEach** etkinliğinin **Items** özelliğini **New Object [] {1, "abc"}** olarak ayarlayın.

5. <xref:System.Activities.Statements.WriteLine>Araç kutusunun **temel öğeler** bölümünden bir etkinliği **MyForEach** etkinliğinin **Delegate: Body** bölümüne sürükleyin.

6. Etkinliğin **Text** özelliğini <xref:System.Activities.Statements.WriteLine> **bağımsız değişken. ToString ()** olarak ayarlayın.

   İş akışı yürütüldüğünde konsol şunları gösterir:

   **1** 
    **ABC**