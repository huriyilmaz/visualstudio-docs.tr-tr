---
title: 'İş Akışı Tasarımcısı: etkinlik temsilcilerini tanımlama ve kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 67e862e3772b157c4a0999ccd44c3698119ae8a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650344"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısı etkinlik temsilcileri tanımlama ve kullanma

.NET Framework 4,5 <xref:System.Activities.Statements.InvokeDelegate> etkinliği için hazır bir tasarımcı içerir. Bu tasarımcı, <xref:System.Activities.ActivityAction> veya <xref:System.Activities.ActivityFunc%601> gibi <xref:System.Activities.ActivityDelegate> türetilen etkinliğe temsilciler atamak için kullanılabilir.

## <a name="define-an-activity-delegate"></a>Etkinlik temsilcisi tanımlama

1. Yeni bir **Iş akışı konsol uygulaması** projesi oluşturun.

   > [!NOTE]
   > **Iş akışı** proje şablonlarını görmüyorsanız, önce Visual Studio 'nun **Windows Workflow Foundation** bileşenini yüklemeniz gerekir. Ayrıntılı yönergeler için bkz. [ınstall Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. **Çözüm Gezgini** projeye sağ tıklayın ve  > **Yeni öğe** **Ekle** ' yi seçin. **Iş akışı** kategorisini seçin ve ardından **etkinlik** öğesi şablonunu seçin. Yeni etkinliği **MyForEach. xaml** olarak adlandırın ve ardından **Tamam**' ı seçin.

   Etkinlik, iş akışı Tasarımcısı 'nda açılır.

4. İş Akışı Tasarımcısı, **bağımsız değişkenler** sekmesine tıklayın.

5. **Bağımsız değişken Oluştur**' a tıklayın. Yeni bağımsız değişken **öğelerini**adlandırın.

6. **Bağımsız değişken türü** sütununda, **[T] dizisini**seçin.

7. Tür tarayıcısında, **nesne** ' yi seçin ve ardından **Tamam**' ı seçin.

8. **Bağımsız değişken Oluştur** ' a tekrar tıklayın. Yeni bağımsız değişken **gövdesini**adlandırın. Yeni bağımsız değişkenin **Yön** sütununda **özellik**' i seçin.

9. Bağımsız değişken türü sütununda **türler Için araştır** ' ı seçin.

10. Tür tarayıcısında, **tür adı** alanına **ActivityAction** girin. Ağaç görünümünde **ActivityAction \<T >** seçin. **ActivityAction > \<Object** türünün bağımsız değişkenine atanması için görüntülenen açılan menüden **nesne** ' yi seçin.

11. Araç kutusunun **Denetim akışı** bölümünden bir <xref:System.Activities.Statements.While> etkinliğini tasarımcı yüzeyine sürükleyin.

12. @No__t_0 etkinliğini seçin ve **değişkenler** sekmesini seçin.

13. **Değişken Oluştur**' u seçin. Yeni değişken **dizinini**adlandırın.

14. **Değişken türü** sütununda **Int32**' yi seçin. **Kapsamı** **sırasında**ve **varsayılan** sütunu boş bırakın.

15. @No__t_1 etkinliğinin **Condition** özelliğini **< Items. length; dizinine**ayarlayın.

16. Araç kutusu ' nu **temel elemanlar** bölümünden bir <xref:System.Activities.Statements.InvokeDelegate> etkinliğini <xref:System.Activities.Statements.While> etkinliğinin **gövdesine** sürükleyin.

17. Temsilci açılan kutusunda **gövde** ' yi seçin.

18. @No__t_1 etkinliğinin **Özellikler** kılavuzunda, **temsilci bağımsız değişkenleri** özelliğindeki **...** düğmesine tıklayın.

19. **Bağımsız değişkenin adlandırılmış bağımsız**değişkeninin **değer** sütununda, **[Dizin] öğesini**girin. **Temsilci bağımsız değişkenleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

20. @No__t_0 etkinliğini <xref:System.Activities.Statements.InvokeDelegate> etkinliğinin altındaki yatay satıra sürükleyin. @No__t_0 etkinliği oluşturulur ve **MyForEach** etkinliğinin **Body** bölümündeki iki etkinliği içermek için bir <xref:System.Activities.Statements.Sequence> etkinliği otomatik olarak oluşturulur. **Body** bölümü yalnızca tek bir etkinlik içerebileceğinden, bu sıra gereklidir. Otomatik olarak yeni bir <xref:System.Activities.Statements.Sequence> etkinliği oluşturmak, .NET Framework 4,5 'nin yeni bir özelliğidir.

21. @No__t_1 etkinliğinin **to** özelliğini **index**olarak ayarlayın. **Assign** etkinliğinin **Value** özelliğini **index + 1**olarak ayarlayın.

    Özel **MyForEach** etkinliği, **öğe** koleksiyonu aracılığıyla kendisine geçirilen her bir değer için bir kez rastgele etkinlik çağırır. bu değerler, etkinliğin girdileri olarak koleksiyondaki değerlerdir.

## <a name="use-the-custom-activity-in-a-workflow"></a>Bir iş akışında özel etkinliği kullanma

1. **Ctrl** +**SHIFT** +**B**'ye basarak projeyi derleyin.

2. **Çözüm Gezgini**, tasarımcıda **Workflow1. xaml** ' yi açın.

3. Araç kutusundan bir **MyForEach** etkinliğini tasarımcı yüzeyine sürükleyin. Etkinlik, araç kutusunun bir bölümünde projeyle aynı adı taşıyan bir bölümdür.

4. **MyForEach** etkinliğinin **Items** özelliğini **New Object [] {1, "abc"}** olarak ayarlayın.

5. Araç kutusunun **temel öğeler** bölümünden bir <xref:System.Activities.Statements.WriteLine> etkinliğini **MyForEach** etkinliğinin **Delegate: Body** bölümüne sürükleyin.

6. @No__t_1 etkinliğinin **Text** özelliğini **Argument. ToString ()** olarak ayarlayın.

İş akışı yürütüldüğünde, konsol aşağıdaki çıktıyı gösterir:

**1** 
**ABC**