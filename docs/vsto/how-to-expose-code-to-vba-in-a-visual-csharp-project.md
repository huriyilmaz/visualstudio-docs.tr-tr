---
title: "Nasıl olur: C# projesinde kodu VBA'ya maruz"
description: İki tür kodun birbiriyle etkileşim kurması için Visual C# Visual Basic for Applications (VBA) kodunun nasıl açığa çıkarılacağını öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9836ba105a3522cc680e865f06f9da078cf9edba
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969066"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Nasıl yap: Visual C# projesinde kodu VBA'ya maruz
  İki tür kodun birbiriyle etkileşim kurması için visual Visual Basic for Applications (VBA) kodu kullanmak için Visual C# projesinde kodu açığa çıkarabilirsiniz.

 Visual C# işlemi, Visual Basic farklıdır. Daha fazla bilgi için, [bkz. How to: Expose code to VBA in a Visual Basic projesinde](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Visual C# projesinde kodu ortaya çıkarma
 VBA kodunun Bir Visual C# projesinde kod çağırmasını etkinleştirmek için, kodu COM'a görünür olacak şekilde değiştirebilir ve ardından tasarımcıda **ReferenceAssemblyFromVbaProject** **özelliğini True** olarak ayarlayın.

 VBA'dan Visual C# projesinde yöntem çağırmayı gösteren bir kılavuz için bkz. Adım adım: Visual C&#35; [projesinde VBA'dan kod çağırma.](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Visual C# projesinde kodu VBA'ya göstermek için

1. Makroları destekleyen ve zaten VBA kodu içeren bir Word belgesini, Excel çalışma kitabını veya Excel şablonu temel alan bir belge düzeyi proje açın veya oluşturun.

    Makroları destekleyen belge dosyası biçimleri hakkında daha fazla bilgi için bkz. [VBA ve belge düzeyinde özelleştirmeleri birleştirme.](../vsto/combining-vba-and-document-level-customizations.md)

   > [!NOTE]
   > Bu özellik Word şablonu projelerinde kullanılamaz.

2. Kullanıcıdan makroları etkinleştirmesi istenmeden belgede VBA kodunun çalışmasına izin verilenin. Word veya Office için Güven Merkezi ayarlarında güvenilir konumlar listesine Office VBA kodunun çalıştırılacağını Excel.

3. VBA'ya göstermek istediğiniz üyeyi projenizin genel sınıfına ekleyin ve yeni üyeyi genel olarak **bildirin.**

4. Aşağıdaki ve <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliklerini VBA'ya açığa çıkararak sınıfa uygulayabilirsiniz. Bu öznitelikler, sınıf arabirimi oluşturmadan sınıfı COM'da görünür hale getirebilirsiniz.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. VBA'ya açığa çıkararak sınıfın bir örneğini geri almak için projenizin konak öğesi sınıfının **GetAutomationObject** yöntemini geçersiz kılın:

   - Bir konak öğesi sınıfını VBA'ya açığa çıkarıyorsanız, bu sınıfa ait **GetAutomationObject** yöntemini geçersiz kılın ve sınıfın geçerli örneğini girin.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - VBA'da konak öğesi olmayan bir sınıfı açığa çıkarıyorsanız, projeniz içinde herhangi bir konak öğesinin **GetAutomationObject** yöntemini geçersiz kılın ve konak dışı öğe sınıfının bir örneğini dönüş. Örneğin, aşağıdaki kod VBA adlı bir sınıfı açığa çıkararak `DocumentUtilities` varsayıyor.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Konak öğeleri hakkında daha fazla bilgi için bkz. [Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

6. VBA'ya açığa çıkarmakta olduğunu sınıftan bir arabirimi ayıklar. Arabirimi **Ayıkla** iletişim kutusunda, arabirim bildirimine dahil etmek istediğiniz ortak üyeleri seçin. Daha fazla bilgi için [bkz. Arabirimi yeniden düzenlemeyi ayıklama.](../ide/reference/extract-interface.md)

7. Arabirim **bildirimine public** anahtar sözcüğünü ekleyin.

8. Arabirime aşağıdaki özniteliği ekleyerek arabirimin <xref:System.Runtime.InteropServices.ComVisibleAttribute> COM'da görünür hale gelir.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. belgesini (Word için) veya çalışma sayfasını (Excel için) içinde tasarımcıda [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açın.

10. Özellikler **penceresinde** **ReferenceAssemblyFromVbaProject** özelliğini seçin ve değeri True olarak **değiştirin.**

    > [!NOTE]
    > Çalışma kitabı veya belge zaten VBA kodu içeriyorsa veya belgedeki VBA kodunun çalışmasına güvenilmiyorsa **ReferenceAssemblyFromVbaProject** özelliğini True olarak ayarsanız bir hata iletisi **alırsınız.** Bunun nedeni Visual Studio vbA projesini değiştirenin bu durumda değiştirileyemilmesidir.

11. Görüntülenen **iletide** Tamam'a tıklayın. Bu ileti, 'den projeyi çalıştırarak çalışma kitabına veya belgeye VBA kodu eklerken VBA kodunun projeyi bir sonraki derlemesinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaybedileceğini anımsatır. Bunun nedeni, projeyi her derlemeniz için derleme çıkış klasöründeki belgenin üzerine yazmasıdır.

     Bu noktada, Visual Studio VBA projesinin derlemeye çağırana kadar projeyi yapılandırıyor. Visual Studio VBA projesine `GetManagedClass` adlı bir yöntem de ekler. VBA'ya açık olan sınıfa erişmek için vbA projesinin herhangi bir yerinden bu yöntemi çağırabilirsiniz.

12. Projeyi derleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [VBA ve belge düzeyi özelleştirmelerini birleştirme](../vsto/combining-vba-and-document-level-customizations.md)
- [Adım adım kılavuz: Visual C&#35; projesinde VBA'dan kod çağırma](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Nasıl olur: Bir Visual Basic projesinde kodu VBA'Visual Basic açığa çıkarma](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
