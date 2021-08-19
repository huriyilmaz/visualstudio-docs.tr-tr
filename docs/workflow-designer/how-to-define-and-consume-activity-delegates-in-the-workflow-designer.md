---
title: Etkinlik temsilcilerini tanımlama ve tüketme
description: İş Akışı Tasarımcısı .NET Framework 4,5 ' de, etkinlik temsilcilerini tanımlamak ve tüketmek için kullanabileceğiniz ınvokedelegate etkinliğinin hazır olmayan bir tasarımcısını nasıl içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 150b3b3ababe9e559cc8fe07d049509348201f08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114725"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında etkinlik temsilcileri tanımlama ve kullanma

.NET Framework 4,5, etkinlik için bir kullanıma hazır tasarımcı içerir <xref:System.Activities.Statements.InvokeDelegate> . Bu tasarımcı, veya gibi öğesinden türetilen etkinliğe temsilciler atamak için kullanılabilir <xref:System.Activities.ActivityDelegate> <xref:System.Activities.ActivityAction> <xref:System.Activities.ActivityFunc%601> .

## <a name="define-an-activity-delegate"></a>Etkinlik temsilcisi tanımlama

1. Yeni bir **Iş akışı konsol uygulaması** projesi oluşturun.

   > [!NOTE]
   > **iş akışı** proje şablonlarını görmüyorsanız, önce Visual Studio **Windows Workflow Foundation** bileşenini yüklemeniz gerekir. ayrıntılı yönergeler için bkz. [ınstall Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. **Çözüm Gezgini** projeye sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Iş akışı** kategorisini seçin ve ardından **etkinlik** öğesi şablonunu seçin. Yeni etkinliği **MyForEach. xaml** olarak adlandırın ve ardından **Tamam**' ı seçin.

   Etkinlik, iş akışı Tasarımcısı 'nda açılır.

4. İş Akışı Tasarımcısı, **bağımsız değişkenler** sekmesine tıklayın.

5. **Bağımsız değişken Oluştur**' a tıklayın. Yeni bağımsız değişken **öğelerini** adlandırın.

6. **Bağımsız değişken türü** sütununda, **[T] dizisini** seçin.

7. Tür tarayıcısında, **nesne** ' yi seçin ve ardından **Tamam**' ı seçin.

8. **Bağımsız değişken Oluştur** ' a tekrar tıklayın. Yeni bağımsız değişken **gövdesini** adlandırın. Yeni bağımsız değişkenin **Yön** sütununda **özellik**' i seçin.

9. Bağımsız değişken türü sütununda **türler Için araştır** ' ı seçin.

10. Tür tarayıcısında, **tür adı** alanına **ActivityAction** girin. Ağaç **görünümünde \<T> ActivityAction** öğesini seçin. **ActivityAction \<Object>** türünün bağımsız değişkenine atanması için görüntülenen açılan menüden **nesne** ' yi seçin.

11. <xref:System.Activities.Statements.While>araç kutusunun **denetim Flow** bölümündeki bir etkinliği tasarımcı yüzeyine sürükleyin.

12. Etkinliği seçin <xref:System.Activities.Statements.While> ve **değişkenler** sekmesini seçin.

13. **Değişken Oluştur**' u seçin. Yeni değişken **dizinini** adlandırın.

14. **Değişken türü** sütununda **Int32**' yi seçin. **Kapsamı** **sırasında** ve **varsayılan** sütunu boş bırakın.

15. Etkinliğin **Condition** özelliğini <xref:System.Activities.Statements.While> **< Items. length; dizinine** göre ayarlayın.

16. <xref:System.Activities.Statements.InvokeDelegate>Araç kutusu ' ndan bir  etkinliği etkinliğin **gövdesine** sürükleyin <xref:System.Activities.Statements.While> .

17. Temsilci açılan kutusunda **gövde** ' yi seçin.

18. Etkinliğin **Özellikler** kılavuzunda <xref:System.Activities.Statements.InvokeDelegate> , **temsilci bağımsız değişkenleri** özelliğindeki **...** düğmesine tıklayın.

19. **Bağımsız değişkenin adlandırılmış bağımsız** değişkeninin **değer** sütununda, **[Dizin] öğesini** girin. **Temsilci bağımsız değişkenleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

20. Etkinliği <xref:System.Activities.Statements.Assign> etkinliğin altındaki yatay çizgiye sürükleyin <xref:System.Activities.Statements.InvokeDelegate> . <xref:System.Activities.Statements.Assign>Etkinlik oluşturulur ve <xref:System.Activities.Statements.Sequence> **MyForEach** etkinliğinin **Body** bölümündeki iki etkinliği içerecek şekilde otomatik olarak bir etkinlik oluşturulur. **Body** bölümü yalnızca tek bir etkinlik içerebileceğinden, bu sıra gereklidir. otomatik olarak yeni bir <xref:System.Activities.Statements.Sequence> etkinlik oluşturulması .NET Framework 4,5 ' nin yeni bir özelliğidir.

21. Etkinliğin **to** özelliğini <xref:System.Activities.Statements.Assign> **index** olarak ayarlayın. **Assign** etkinliğinin **Value** özelliğini **index + 1** olarak ayarlayın.

    Özel **MyForEach** etkinliği, **öğe** koleksiyonu aracılığıyla kendisine geçirilen her bir değer için bir kez rastgele etkinlik çağırır. bu değerler, etkinliğin girdileri olarak koleksiyondaki değerlerdir.

## <a name="use-the-custom-activity-in-a-workflow"></a>Bir iş akışında özel etkinliği kullanma

1. **CTRL** + **SHIFT** + **B** tuşlarına basarak projeyi derleyin.

2. **Çözüm Gezgini**, tasarımcıda **Workflow1. xaml** ' yi açın.

3. Araç kutusundan bir **MyForEach** etkinliğini tasarımcı yüzeyine sürükleyin. Etkinlik, araç kutusunun bir bölümünde projeyle aynı adı taşıyan bir bölümdür.

4. **MyForEach** etkinliğinin **Items** özelliğini **New Object [] {1, "abc"}** olarak ayarlayın.

5. <xref:System.Activities.Statements.WriteLine>Araç kutusunun **temel öğeler** bölümünden bir etkinliği **MyForEach** etkinliğinin **Delegate: Body** bölümüne sürükleyin.

6. Etkinliğin **Text** özelliğini <xref:System.Activities.Statements.WriteLine> **bağımsız değişken. ToString ()** olarak ayarlayın.

İş akışı yürütüldüğünde, konsol aşağıdaki çıktıyı gösterir:

**1** 
 **ABC**
