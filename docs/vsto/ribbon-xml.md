---
title: Şerit XML
description: Şerit (görsel Tasarımcı) öğesi tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız şerit (XML) öğesini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 69ca0269859db9e1a69904c2211b8f4d1ad45710
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879299"
---
# <a name="ribbon-xml"></a>Şerit XML
  Şerit (XML) öğesi, XML kullanarak bir şeridi özelleştirmenize olanak sağlar. Şeriti şerit (görsel Tasarımcı) öğesi tarafından desteklenmeyen bir şekilde özelleştirmek istiyorsanız şerit (XML) öğesini kullanın. Her öğe ile yapabileceklerinize ilişkin bir karşılaştırma için bkz. [Şerit 'e genel bakış](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Bir projeye Şerit (XML) öğesi ekleme
 **Yeni öğe Ekle** iletişim kutusundan herhangi bir Office projesine **Şerit (XML)** öğesi ekleyebilirsiniz. Visual Studio projenize otomatik olarak aşağıdaki dosyaları ekler:

- Şerit XML dosyası. Bu dosya, Şerit kullanıcı arabirimini (UI) tanımlar. Sekmeler, gruplar ve denetimler gibi kullanıcı arabirimi öğelerini eklemek için bu dosyayı kullanın. Ayrıntılar için bu konunun ilerleyen kısımlarında yer alarak [ŞERIT XML dosya başvurusu](#RibbonDescriptorFile) bölümüne bakın.

- Şerit kod dosyası. Bu dosya *Şerit sınıfını* içerir. Bu sınıf, **Yeni öğe Ekle** Iletişim kutusunda **Şerit (XML)** öğesi için belirttiğiniz ada sahiptir. Microsoft Office uygulamalar özel şeridi yüklemek için bu sınıfın bir örneğini kullanır. Ayrıntılar için bu konunun ilerleyen kısımlarında yer alarak [Ribbon Class Reference](#RibbonExtensionClass) bölümüne bakın.

  Varsayılan olarak, bu dosyalar Şeritteki **Eklentiler sekmesine özel bir grup ekler.**

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Microsoft Office uygulamasında özel şeridi görüntüleme
 Projenize **Şerit (XML)** öğesi ekledikten sonra, yöntemi geçersiz kılan **ThisAddIn**, **ThisWorkbook** veya **THISDOCUMENT** sınıfına kod eklemeniz gerekir `CreateRibbonExtensibilityObject` ve Şerit XML sınıfını Office uygulamasına geri döndürür.

 Aşağıdaki kod örneği, yöntemini geçersiz kılar `CreateRibbonExtensibilityObject` ve MyRibbon adlı bir ŞERIT XML sınıfı döndürür.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Özel şeridin davranışını tanımlama
 *Geri çağırma yöntemleri* oluşturarak Şeritteki bir düğmeye tıklanması gibi kullanıcı eylemlerine yanıt verebilirsiniz. Geri çağırma yöntemleri Windows Forms denetimlerindeki olaylara benzer, ancak UI öğesinin XML dosyasındaki bir öznitelik tarafından tanımlanır. Yöntemleri şerit sınıfına yazdığınızda, bir denetim öznitelik değeriyle aynı ada sahip olan yöntemi çağırır. Örneğin, bir Kullanıcı Şeritteki bir düğmeye tıkladığında çağrılan bir geri çağırma yöntemi oluşturabilirsiniz. Bir geri çağırma yöntemi oluşturmak için iki adım gereklidir:

- Kodunuzda bir geri çağırma yöntemi tanımlayan Şerit XML dosyasındaki bir denetime öznitelik atayın.

- Şerit sınıfında geri çağırma yöntemini tanımlayın.

> [!NOTE]
> Outlook ek bir adım gerektirir. Daha fazla bilgi için bkz. [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).

 Bir uygulamayı şeritten nasıl otomatikleştirebileceğinizi gösteren bir anlatım için bkz. [Izlenecek yol: ŞERIT XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Denetimlere geri çağırma yöntemleri atama
 Şerit XML dosyasındaki bir denetime geri çağırma yöntemi atamak için, geri çağırma yönteminin türünü ve yöntemin adını belirten bir öznitelik ekleyin. Örneğin, aşağıdaki öğe adlı bir **OnAction** geri çağırma yöntemine sahip bir iki durumlu düğmeyi tanımlar `OnToggleButton1` .

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 Kullanıcı belirli bir denetimle ilişkili ana görevi gerçekleştirdiğinde, **OnAction** çağrılır. Örneğin, Kullanıcı düğmeye tıkladığında iki durumlu düğmenin **OnAction** geri çağırma yöntemi çağırılır.

 Özniteliğinde belirttiğiniz yöntemi herhangi bir ada sahip olabilir. Ancak, Şerit kod dosyasında tanımladığınız yöntemin adıyla eşleşmesi gerekir.

 Şerit denetimlerine atayabileceğiniz birçok farklı türde geri arama yöntemi vardır. Her denetim için kullanılabilen geri çağırma yöntemlerinin tüm listesi için bkz. [geliştiriciler Için Office (2007) Şerit kullanıcı arabirimini özelleştirme (3. kısım)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))teknik makalesi.

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Geri çağırma yöntemlerini tanımlama
 Şerit kod dosyasındaki Şerit sınıfında geri çağırma yöntemlerinizi tanımlayın. Bir geri çağırma yönteminde birkaç gereksinim vardır:

- Ortak olarak bildirilmelidir.

- Adının, Şerit XML dosyasındaki bir denetime atadığınız geri çağırma yönteminin adıyla eşleşmesi gerekir.

- İmzası, ilişkili şerit denetimi için kullanılabilen bir geri arama yöntemi türünün imzasıyla eşleşmelidir.

  Şerit denetimleri için geri çağırma yöntemi imzalarının tüm listesi için bkz. [geliştiriciler Için Office (2007) Şerit kullanıcı arabirimini özelleştirme (3. Kısım 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12))teknik makalesi. Visual Studio, Şerit kod dosyasında oluşturduğunuz geri çağırma yöntemleri için IntelliSense desteği sağlamaz. Geçerli bir imzayla eşleşmeyen bir geri çağırma yöntemi oluşturursanız, kod derlenir, ancak Kullanıcı denetime tıkladığında hiçbir şey olmaz.

  Tüm geri çağırma yöntemlerinin <xref:Microsoft.Office.Core.IRibbonControl> , yöntemi çağıran denetimi temsil eden bir parametresi vardır. Bu parametreyi, birden fazla denetim için aynı geri çağırma yöntemini yeniden kullanmak için kullanabilirsiniz. Aşağıdaki kod örneğinde, kullanıcının tıkladığı denetime bağlı olarak farklı görevler gerçekleştiren bir **OnAction** geri çağırma yöntemi gösterilmektedir.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Şerit XML dosyası başvurusu
 Şerit XML dosyasına öğeler ve öznitelikler ekleyerek özel şeritlerinizi tanımlayabilirsiniz. Varsayılan olarak, Şerit XML dosyası aşağıdaki XML 'i içerir.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 Aşağıdaki tabloda, Şerit XML dosyasındaki varsayılan öğeler açıklanmaktadır.

|Öğe|Açıklama|
|-------------|-----------------|
|**Customuı**|VSTO eklenti projesindeki özel şeridi temsil eder.|
|**şeridi**|Şeridi temsil eder.|
|**sıralanan**|Bir Şerit sekmeleri kümesini temsil eder.|
|**sekmesinde**|Tek bir şerit sekmesini temsil eder.|
|**grup**|Şerit sekmesindeki bir denetim grubunu temsil eder.|

 Bu öğelerin, özel şeridin görünümünü ve davranışını belirten öznitelikleri vardır. Aşağıdaki tabloda, Şerit XML dosyasındaki varsayılan öznitelikler açıklanmaktadır.

|Öznitelik|Üst öğe|Description|
|---------------|--------------------|-----------------|
|**onLoad**|**Customuı**|Uygulama Şeriti yüklediğinde çağrılan bir yöntemi tanımlar.|
|**ıdmso**|**sekmesinde**|Şeritte görüntülenecek yerleşik bir sekmeyi tanımlar.|
|**id**|**grup**|Grubu tanımlar.|
|**etiketin**|**grup**|Grupta görüntülenen metni belirtir.|

 Şerit XML dosyasındaki varsayılan öğeler ve öznitelikler, kullanılabilen öğelerin ve özniteliklerin küçük bir alt kümesidir. Kullanılabilir öğelerin ve özniteliklerin tüm listesi için bkz. [geliştiriciler Için Office (2007) Şerit kullanıcı arabirimini özelleştirme (Bölüm 2/3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12))teknik makalesi.

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Şerit sınıfı başvurusu
 Visual Studio, Şerit kod dosyasında Şerit sınıfını oluşturur. Şeritteki denetimlerin geri çağırma yöntemlerini bu sınıfa ekleyin. Bu sınıf, <xref:Microsoft.Office.Core.IRibbonExtensibility> arabirimini uygular.

 Aşağıdaki tabloda bu sınıftaki varsayılan yöntemler açıklanmıştır.

|Yöntem|Açıklama|
|------------|-----------------|
|`GetCustomUI`|Şerit XML dosyasının içeriğini döndürür. Microsoft Office uygulamalar, özel şeritlerinizin Kullanıcı arabirimini tanımlayan bir XML dizesi almak için bu yöntemi çağırır. Bu yöntem yöntemini uygular <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Note:** `GetCustomUI` yalnızca Şerit XML dosyasının içeriğini döndürmek için uygulanmalıdır; VSTO eklentisini başlatmak için kullanılmamalıdır.   Özellikle, uygulamanızda iletişim kutularını veya diğer pencereleri görüntülemeyi denememelisiniz `GetCustomUI` . Aksi takdirde, özel şerit düzgün çalışmayabilir. VSTO eklentisini başlatan kodu çalıştırmak istiyorsanız `ThisAddIn_Startup` olay işleyicisine kodu ekleyin.|
|`OnLoad`|<xref:Microsoft.Office.Core.IRibbonControl>Parametreyi `Ribbon` alana atar. Microsoft Office uygulamalar, özel şeridi yüklediklerinde bu yöntemi çağırır. Özel şeridi dinamik olarak güncelleştirmek için bu alanı kullanabilirsiniz. Daha fazla bilgi için bkz. [geliştiriciler Için Office (2007) Şerit kullanıcı arabirimini özelleştirme (Bölüm 1/3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12))teknik makalesi.|
|`GetResourceText`|`GetCustomUI`ŞERIT XML dosyasının içeriğini almak için yöntemi tarafından çağırılır.|

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
