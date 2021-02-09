---
title: 'Nasıl yapılır: C# projesinde kodu VBA kullanımına sunma'
description: İki tür kodun birbirleriyle etkileşime geçmesini isterseniz, bir Visual C# projesindeki kodu Visual Basic for Applications (VBA) koduna nasıl kullanıma sunabileceğinizi öğrenin.
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1df1eed4edec3efdbf93f4effc352b3d02656d04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889414"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Nasıl yapılır: Visual C# projesinde kodu VBA kullanımına sunma
  İki tür kodun birbirleriyle etkileşime geçmesini isterseniz, bir Visual C# projesindeki kodu Visual Basic for Applications (VBA) kodu olarak kullanıma sunabilirsiniz.

 Visual C# işlemi Visual Basic işlemden farklıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)sunma.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Visual C# projesinde kodu kullanıma sunma
 VBA kodunu bir Visual C# projesindeki kodu çağırmak üzere etkinleştirmek için, kodu COM 'a görünür olacak şekilde değiştirin ve ardından, tasarımcıda **ReferenceAssemblyFromVbaProject** özelliğini **true** olarak ayarlayın.

 Visual C# projesinde VBA 'dan bir yöntemin nasıl çağrılacağını gösteren bir anlatım için bkz. [Izlenecek yol: Visual C&#35; PROJESINDEKI VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Visual C# projesindeki kodu VBA 'da ortaya çıkarmak için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonunu temel alan belge düzeyinde bir proje açın veya oluşturun.

    Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Bu özellik Word şablon projelerinde kullanılamaz.

2. Belgedeki VBA kodunun, kullanıcıdan makroları etkinleştirmesini istemeden çalışmasına izin verildiğinden emin olun. Office projesinin konumunu, Word veya Excel için Güven Merkezi ayarlarındaki güvenilir konumlar listesine ekleyerek çalıştırmak için VBA koduna güvenebilirsiniz.

3. VBA 'ya göstermek istediğiniz üyeyi projenizdeki ortak bir sınıfa ekleyin ve yeni üyeyi **ortak** olarak bildirin.

4. Aşağıdaki <xref:System.Runtime.InteropServices.ComVisibleAttribute> ve <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliklerini VBA 'da ortaya çıkardığınız sınıfa uygulayın. Bu öznitelikler sınıfı COM olarak görünür hale getirir, ancak bir sınıf arabirimi üretmeyecektir.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. VBA 'da kullanıma sunmanıza yardımcı olan bir sınıfın örneğini döndürmek için projenizdeki bir konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın:

   - VBA için bir konak öğesi sınıfı kullanıma sunıyorsanız, bu sınıfa ait **GetAutomationObject** yöntemini geçersiz kılın ve sınıfın geçerli örneğini döndürün.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Konak öğesi olmayan bir sınıfı VBA 'ya çıkarıyorsanız, projenizdeki herhangi bir konak öğesinin **GetAutomationObject** yöntemini geçersiz kılın ve konak olmayan öğe sınıfının bir örneğini döndürün. Örneğin, aşağıdaki kod, VBA 'ya adlı bir sınıfı kullanıma sunduğunuzu varsayar `DocumentUtilities` .

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

6. VBA 'da ortaya çıkardığınız sınıftan bir arabirim ayıklayın. **Arabirimi Ayıkla** iletişim kutusunda, arabirim bildirimine eklemek istediğiniz ortak üyeleri seçin. Daha fazla bilgi için bkz. [arabirimi yeniden düzenlemeyi ayıklama](../ide/reference/extract-interface.md).

7. Arabirim bildirimine **ortak** anahtar sözcük ekleyin.

8. Arabirimine aşağıdaki özniteliği ekleyerek arabirimi COM 'a görünür hale getirin <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. İçindeki tasarımcıda belgeyi (Word için) veya çalışma sayfasını (Excel için) açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. **Özellikler** penceresinde, **ReferenceAssemblyFromVbaProject** özelliğini seçin ve değeri **true** olarak değiştirin.

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içermiyorsa veya belgedeki VBA kodunun çalıştırılmak üzere güvenilir olmaması durumunda, **ReferenceAssemblyFromVbaProject** özelliğini **true** olarak ayarladığınızda bir hata iletisi alırsınız. Bunun nedeni, Visual Studio 'Nun belgedeki VBA projesini değiştiremeyeceği durumdur.

11. Görüntülenen iletide **Tamam** ' a tıklayın. Bu ileti, projeyi ' den çalıştırırken çalışma kitabına veya belgeye VBA kodu eklerseniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , projeyi bir sonraki sefer OLUŞTURDUĞUNUZDA VBA kodunun kaybolacağını hatırlatır. Bunun nedeni, projeyi her oluşturduğunuzda derleme çıkış klasöründeki belgenin üzerine yazılır.

     Bu noktada, Visual Studio projeyi VBA projesinin derlemeye çağırabilmesi için yapılandırır. Visual Studio, VBA projesine adlı bir yöntemi de ekler `GetManagedClass` . VBA 'da gösterilen sınıfa erişmek için VBA projesinin herhangi bir yerinden bu yöntemi çağırabilirsiniz.

12. Projeyi derleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [İzlenecek yol: Visual C&#35; projesindeki VBA 'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Nasıl yapılır: Visual Basic projesindeki kodu VBA 'de kullanıma sunma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
