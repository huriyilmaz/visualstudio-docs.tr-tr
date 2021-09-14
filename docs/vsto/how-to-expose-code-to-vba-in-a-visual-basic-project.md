---
title: "Nasıl olur: Bir Visual Basic projesinde kodu VBA'Visual Basic açığa çıkarma"
description: İki tür kodun birbiriyle etkileşim kurması Visual Basic kod Visual Basic for Applications (VBA) kodu kullanmak için bir Visual Basic projesinde kodu nasıl ortaya çıkarabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a943688945ab7134742ff85ec63e7fad5a4f11c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725587"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>Nasıl olur: Bir Visual Basic projesinde kodu VBA'Visual Basic açığa çıkarma
  İki tür kodun birbiriyle etkileşim kurması Visual Basic for Applications projesinde kodun [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] (VBA) kodunun nasıl açığa çıkarılacağını ortaya çıkarabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bu Visual Basic Visual C# sürecinden farklıdır. Daha fazla bilgi için, [bkz. How to: Expose code to VBA in a Visual C&#35; projesinde](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

 bir konak öğesi sınıfındaki kod için işlem, diğer sınıflarda koda göre farklıdır:

- [Konak öğesi sınıfında kodu açığa çıkarma](#HostItemCode)

- [Konak öğesi sınıfında yer alan kodu açığa çıkarma](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a> Konak öğesi sınıfında kodu açığa çıkarma
 VBA kodunun bir konak öğesi sınıfındaki Visual Basic çağıracağını etkinleştirmek için konak öğesinin **EnableVbaCallers** özelliğini True olarak **ayarlayın.**

 Bir konak öğesi sınıfının yönteminin nasıl açığa çıkarılacağını ve vbA'dan nasıl çağrılacağını gösteren bir kılavuz için bkz. [Walkthrough: Call code from VBA in a Visual Basic projesinde](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md). Konak öğeleri hakkında daha fazla bilgi için bkz. [Konak öğeleri ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>Bir konak öğesinde kodu VBA'ya göstermek için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonu temel alan bir belge düzeyi proje açın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] veya oluşturun.

     Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

    > [!NOTE]
    > Bu özellik Word şablonu projelerinde kullanılamaz.

2. Kullanıcıdan makroları etkinleştirmesi istenmeden belgede VBA kodunun çalışmasına izin verilenin. Word veya Office için Güven Merkezi ayarlarında güvenilir konumlar listesine Office VBA kodunun çalışmasına Excel.

3. VBA'ya göstermek istediğiniz özelliği, yöntemi veya olayı projenizin konak öğesi sınıflarından biri olarak ekleyin ve yeni üyeyi Genel olarak **bildirin.** Sınıfın adı uygulamaya bağlıdır:

    - Bir Word projesinde, konak öğesi sınıfı varsayılan `ThisDocument` olarak adlandırılmıştır.

    - Bir Excel, konak öğesi sınıfları varsayılan olarak `ThisWorkbook` `Sheet1` , , ve olarak `Sheet2` `Sheet3` adlandırılmıştır.

4. Konak öğesi **için EnableVbaCallers** özelliğini True olarak **ayarlayın.** Bu özellik, konak **öğesi** tasarımcıda açık olduğunda Özellikler penceresinde kullanılabilir.

     Bu özelliği ayardikten sonra, Visual Studio **ReferenceAssemblyFromVbaProject** özelliğini otomatik olarak True olarak **ayarlar.**

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içeriyorsa veya belgede VBA kodunun çalışmasına güvenilmiyorsa **EnableVbaCallers** özelliğini True olarak ayarsanız bir hata iletisi **alırsınız.** Bunun nedeni Visual Studio belgede VBA projesini değiştirenin bu durumda değiştirileyemilmesidir.

5. Görüntülenen **iletide** Tamam'a tıklayın. Bu ileti, proje üzerinde çalışırken çalışma kitabına veya belgeye VBA kodu eklerken projeyi bir sonraki derlemesinde VBA kodunun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaybedileceğini anımsatır. Bunun nedeni, projeyi her derlemeniz için derleme çıkış klasöründeki belgenin üzerine yazmasıdır.

     Bu noktada, Visual Studio VBA projesinin derlemeye çağırana kadar projeyi yapılandırıyor. Visual Studio VBA projesinde `CallVSTOAssembly` , , , veya `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` `Sheet3` modülüne adlı bir özellik de ekler. BU özelliği, VBA'ya açık durumdaki sınıfın ortak üyelerine erişmek için kullanabilirsiniz.

6. Projeyi derleyin.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a> Konak öğesi sınıfında yer alan kodu açığa çıkarma
 VBA kodunun konak öğesi Visual Basic kodu çağıracağını etkinleştirmek için, kodu VBA'ya görünür olacak şekilde değiştirebilirsiniz.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>Bir konak öğesi sınıfında yer alan kodu VBA'ya göstermek için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonu temel alan bir belge düzeyi proje açın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] veya oluşturun.

     Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

    > [!NOTE]
    > Bu özellik Word şablonu projelerinde kullanılamaz.

2. Kullanıcıdan makroları etkinleştirmesi istenmeden belgede VBA kodunun çalışmasına izin verilenin. Word veya Office için Güven Merkezi ayarlarında güvenilir konumlar listesine Office VBA kodunun çalışmasına Excel.

3. VBA'ya göstermek istediğiniz üyeyi projenizin genel sınıfına ekleyin ve yeni üyeyi genel olarak **bildirin.**

4. Aşağıdaki ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualBasic.ComClassAttribute> özniteliklerini VBA'ya açığa çıkararak sınıfa uygulayabilirsiniz. Bu öznitelikler sınıfı VBA'ya görünür hale gelir.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. VBA'ya açığa çıkararak sınıfın bir örneğini geri almak için projenizin konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın. Aşağıdaki kod örneğinde adlı bir sınıfı VBA'ya açığa `DocumentUtilities` çıkarabilirsiniz.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. içinde belge (Word için) veya çalışma sayfası (Excel) tasarımcısını [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açın.

7. Özellikler **penceresinde** **ReferenceAssemblyFromVbaProject** özelliğini seçin ve değeri True olarak **değiştirin.**

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içeriyorsa veya belgedeki VBA kodunun çalışmasına güvenilmiyorsa **ReferenceAssemblyFromVbaProject** özelliğini True olarak ayarsanız bir hata iletisi **alırsınız.** Bunun nedeni Visual Studio belgede VBA projesini değiştirenin bu durumda değiştirileyemilmesidir.

8. Görüntülenen **iletide** Tamam'a tıklayın. Bu ileti, proje üzerinde çalışırken çalışma kitabına veya belgeye VBA kodu eklerken projeyi bir sonraki derlemesinde VBA kodunun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaybedileceğini anımsatır. Bunun nedeni, projeyi her derlemeniz için derleme çıkış klasöründeki belgenin üzerine yazmasıdır.

     Bu noktada, Visual Studio VBA projesinin derlemeye çağırana kadar projeyi yapılandırıyor. Visual Studio VBA projesine `GetManagedClass` adlı bir yöntem de ekler. VBA'ya açık olan sınıfa erişmek için vbA projesinin herhangi bir yerinden bu yöntemi çağırabilirsiniz.

9. Projeyi derleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Adım adım kılavuz: Visual Basic projesinde VBA'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Nasıl olur: Visual C görsel projesinde kodu VBA'&#35; açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
