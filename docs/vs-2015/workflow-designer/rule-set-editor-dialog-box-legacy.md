---
title: Kural kümesi Düzenleyicisi Iletişim kutusu (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8010bbbc38dee980ebe89dc60ccb513379103a26
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846323"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Kural Kümesi Düzenleyicisi İletişim Kutusu (Eski)
Bu konu başlığı altında, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)]**kural kümesi Düzenleyicisi** iletişim kutusunun nasıl kullanılacağı açıklanmaktadır. Eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] hedeflemek gerektiğinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 **Kural kümesi Düzenleyicisi** iletişim kutusu, bir. Rules dosyasına serileştirilmiş olan [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) kural kümelerini oluşturmak ve değiştirmek için kullanılır.

> [!NOTE]
> **Kodlama Ile xml Düzenleyicisi**ile. Rules dosyasını açmak isterseniz, önce iş akışı veya etkinliğin ilişkili Tasarımcı penceresini kapatmanız gerekir.

 **Kural kümesi Düzenleyicisi** iletişim kutusuna erişme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir PolicyActivity kural kümesi oluşturma (eski)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemek için kullanılan eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kural Düzenleyicisi Çoklu hedefleme 'yi desteklemez.

 Aşağıdaki tabloda **kural kümesi Düzenleyicisi** iletişim kutusunun kullanıcı ARABIRIMI (UI) öğeleri açıklanmaktadır.

|Arabirim Öğesi|Açıklama|
|----------------|-----------------|
|**Kural Ekle**|Kural kümesine yeni bir kural tanımı ekler.|
|**Delete**|Seçili kuralı kural kümesinden siler.|
|**İlerek**|Kural kümesiyle hangi türde bir iletme zincirin kullanılacağını belirtir. Şu seçenekler sağlanır:<br /><br /> Tüm ileri zincirleme mekanizmaların kullanılacağını belirten **tam zincirleme**-   : örtük, yöntem Attributing ve bir **Update** işlevi kullanılarak açık.<br />herhangi bir iletme zincirin kullanılacağını belirten -   **sıralı**.<br />Yalnızca **güncelleştirme** eylemlerinde ileri zincirleme yapmayı belirten **yalnızca açık güncelleştirme**-   .<br /><br /> İleri zincirleme hakkında daha fazla bilgi için bkz. [PolicyActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb675229.aspx).|
|**Ad**|Kural kümesi listesi sütun başlığı. Kuralların listesini ada göre sıralamak için tıklayın.|
|**Öncelik**|Kural kümesi listesi sütun başlığı. Kuralların listesini önceliğe göre sıralamak için tıklayın.|
|**Yeniden değerlendirme**|Kural kümesi listesi sütun başlığı. Kural listesini yeniden değerleme türüne göre sıralamak için tıklayın.|
|**Kural önizlemesi**|Kural kümesi listesi sütun başlığı. Kural listesini bir kuralın koşulunun ve eylemlerinin önizlemesine göre sıralamak için tıklayın.|
|**Ad:**|Kural adını girin.|
|**Priority**|Kural için bir öncelik girin. Varsayılan öncelik 0 ' dır.|
|**Yeniden değerlendirme**|Kuralla ne tür bir kuralın kullanılması gerektiğini belirtir. Şu seçenekler sağlanır:<br /><br /> **her zaman**-   , kuralın gerektiği şekilde yeniden değerlendirilmesine neden olur.<br />kuralın **hiçbir şekilde yeniden**değerlendirilmesine neden olan -   . Bu durumda bir kural yalnızca bir kez yürütülür.|
|**Etkin**|Kuralı etkin hale getirmek için işaretleyin.|
|**Koşul**|Kural koşulu için bir ifade girin. İfade sözdizimi hakkında daha fazla bilgi için, bu sayfanın "koşul ve eylem Ifadelerini girme" bölümüne bakın.|
|**Sonra eylemler:**|Eylemler için ifade girin. İfade sözdizimi hakkında daha fazla bilgi için, bu sayfanın "koşul ve eylem Ifadelerini girme" bölümüne bakın.|
|**Else eylemleri:**|Else eylemleri için ifade girin. İfade sözdizimi hakkında daha fazla bilgi için, bu sayfanın "koşul ve eylem Ifadelerini girme" bölümüne bakın.|
|**Tamam**|Kural kümesini bir. Rules dosyasına kaydetmek için tıklayın.|

 Kural kümeleri hakkında daha fazla bilgi için bkz. [PolicyActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="entering-condition-and-action-expressions"></a>Koşul ve eylem Ifadelerini girme
 Koşul için ifadeler ve sonra **kural kümesi Düzenleyicisi** iletişim kutusunda ilgili metin kutularına metin olarak diğer eylemler girersiniz. **Bunu yazabilirsiniz.** bir IntelliSense-Type menü kullanılarak iş akışında kullanılan alanlara, özelliklere ve yöntemlere başvurmak için düzenleyiciye. Ya da doğrudan bir iş akışı üye adı yazabilirsiniz. Sınıf adını ve ardından yöntem adını yazarak, başvurulan türlerde statik yöntemleri çağırabilirsiniz.

 Koşula mantıksal işleçler ekleyebilirsiniz, örneğin ve, veya. Ayrıca, koşullar da ekleyebilirsiniz. Bir koşul, ikili bir işleçtir ve iki işleçtir. Desteklenen ikili işleçler şunlardır = =, >, \<, > = ve < =. Desteklenen işlenenler sabit değer, aritmetik işlev ve kapsamlı ortak üyeleridir.

 Karşılaştırma için türü belirtebilir ve **null** ya da boş bir dize ile karşılaştırabilirsiniz. Karmaşık bir tür içeren bir değişkende yapılan çağrıları, örneğin, `this.Address.State == "WA"`iç içe geçirebilirsiniz.

 İfadeler aşağıdaki işleçleri destekler:

- İlişkisel işleçler: = =, =,! =

- Karşılaştırma işleçleri: <, \<=, >, > =

- Aritmetik işleçler: +,-, *,/, MOD

- Mantıksal işleçler: ve, & &, veya, &#124; &#124;, Not,!

- Bit düzeyinde işleçler: &,&#124;

  İfade işleci önceliği, C# işleç öncelik kurallarını izler.

  Koşullar hakkında daha fazla bilgi için bkz. [Iş akışlarında koşulları kullanma](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Durdur ve Işlevleri Güncelleştir
 **Sonra eylemler:** ve **Else eylemleri:** ifadeler, **durdurmak** ve işlevleri **güncelleştirmek** için destek. **Durdur** işlevini kullanmak için, bir **sonra eyleme** **Durdur** yazın: veya **Else eylemi:** metin kutusu. Durdurma **eylemi,** kural kümesi yürütmenin hemen durdurulmasına neden olur ve denetim, çağırma koduna döner. **Update** işlevini iletme zinciriyle birlikte kullanırsınız.

 Bir **Update** ifadesi, düzenleyicide iki formdan birindeki ifade edilebilir. Her iki form da aşağıdaki örnekte gösterilmiştir:

```
Update(this.Address.State)
Update("this/Address/State")
```

 İleri zincirleme ile **güncelleştirme** kullanma hakkında daha fazla bilgi için, bkz. [PolicyActivity etkinliğini kullanma](https://msdn2.microsoft.com/library/bb675229.aspx).

## <a name="see-also"></a>Ayrıca Bkz.
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [iş akışlarında koşullar kullanılarak](https://msdn2.microsoft.com/library/bb628447.aspx) [PolicyActivity etkinliğini kullanarak](https://msdn2.microsoft.com/library/bb675229.aspx) [kural kümesi seçme iletişim kutusu (eski)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
