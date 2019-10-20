---
title: 'Nasıl yapılır: .NET Framework bir sürümünü hedefleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670617"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Nasıl Yapılır: .NET Framework Sürümü Hedefleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, proje oluştururken bir .NET Framework sürümünü hedefleyen bir projenin nasıl oluşturulacağını ve varolan bir Visual Basic, Visual C# veya Visual F# projesinde hedeflenen sürümün nasıl değiştirileceğini belirtir.

> [!IMPORTANT]
> C++ Projelerin hedef sürümünü değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **Bu konuda**

- [Bir projeyi oluştururken bir sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Hedef sürümü değiştirme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="bkmk_new"></a>Bir projeyi oluştururken bir sürümü hedefleme
 Bir proje oluştururken, hedeflediğiniz .NET Framework sürümü hangi şablonları kullanabileceğinizi belirler.

> [!NOTE]
> Visual Studio 'nun Express sürümlerinde, önce projeyi oluşturmanız gerekir, sonra hedef [sürümü değiştirme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) bu konunun ilerleyen kısımlarında açıklandığı gibi hedefi değiştirebilirsiniz.

#### <a name="to-target-a-version-when-you-create-a-project"></a>Projenizi oluştururken bir sürümü hedeflemek için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunun üst kısmındaki listede, projenizin hedeflemesini istediğiniz .NET Framework sürümünü seçin.

    > [!NOTE]
    > Normalde, yalnızca bir .NET Framework sürümü Visual Studio ile birlikte yüklenir. Başka bir sürümü hedeflemek istiyorsanız, önce bu sürümün yüklü olduğundan emin olmalısınız. Bkz. [Visual Studio multi-hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md).

3. Yüklü şablonlar listesinde, oluşturmak istediğiniz proje türünü seçin, projeyi adlandırın ve **Tamam** düğmesini seçin.

     Şablon listesi yalnızca seçtiğiniz .NET Framework sürümünün desteklediği projeleri gösterir.

## <a name="bkmk_existing"></a>Hedef sürümü değiştirme
 Bu yordamı izleyerek, bir Visual Basic, görsel C#veya visual F# projesinde .NET Framework hedeflenen sürümünü değiştirebilirsiniz.

#### <a name="to-change-the-targeted-version"></a>Hedeflenen sürümü değiştirmek için

1. **Çözüm Gezgini**, değiştirmek istediğiniz projenin kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

     ![Visual Studio Çözüm Gezgini özellikleri](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > C++ Projelerin hedef sürümünü değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. Özellikler penceresinin sol sütununda **uygulama** sekmesini seçin.

     ![Visual Studio uygulama özellikleri uygulama sekmesi](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Bir Windows Mağazası uygulaması oluşturduktan sonra, Windows 'un veya .NET Framework hedeflenen sürümünü değiştiremezsiniz.

3. **Hedef çerçeve** listesinde, istediğiniz sürümü seçin.

4. Görüntülenen doğrulama iletişim kutusunda **Evet** düğmesini seçin.

     Projenin yüklemesi kaldırılır. Yeniden yüklediğinde, seçtiğiniz .NET Framework sürümünü hedefler.

    > [!NOTE]
    > Kodunuz hedeflediğinizden farklı bir .NET Framework sürümüne başvurular içeriyorsa, kodu derlediğinizde veya çalıştırdığınızda hata iletileri görülebilir. Bu hataları gidermek için başvuruları değiştirmeniz gerekir. Bkz. [.NET Framework Hedefleme hatalarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio çoklu hedefleme](../ide/visual-studio-multi-targeting-overview.md) [.NET Framework, ASP.NET Web projeleri için çoklu](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) sürüm belirleme, [hata giderme .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md) [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [projeleri yapılandırma](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) [nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
