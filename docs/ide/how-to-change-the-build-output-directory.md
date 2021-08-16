---
title: 'Nasıl yapılır: derleme çıkış dizinini değiştirme'
description: Projeniz tarafından her yapılandırma temelinde oluşturulan çıktının konumunu nasıl belirtebileceğiniz hakkında bilgi edinin (hata ayıklama, yayın veya her ikisi için).
ms.custom: SEO-VS-2020
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b68fa95d069ab55de1d81caa27697930a8f715f254a226db55a9a32ea74c2d31
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413159"
---
# <a name="how-to-change-the-build-output-directory"></a>Nasıl yapılır: derleme çıkış dizinini değiştirme

Projeniz tarafından oluşturulan çıktının yapılandırma bazında (hata ayıklama, yayın veya her ikisi için) konumunu belirtebilirsiniz.

## <a name="change-the-build-output-directory"></a>Derleme çıkış dizinini değiştirme

1. Projenin özellik sayfalarını açmak için **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

2. Proje türüne göre uygun sekmeyi seçin:

   - C# için **derleme** sekmesini seçin.
   - Visual Basic için **derle** sekmesini seçin.
   - C++ veya JavaScript için **genel** sekmesini seçin.

3. Üstteki yapılandırma açılır penceresinde çıkış dosyası konumunu değiştirmek istediğiniz yapılandırmayı (**hata ayıklama**, **yayın** veya **tüm yapılandırmalar**) seçin.

4. Proje türüne göre farklılık gösteren sayfada çıkış yolu girişini bulun &mdash; :

   - C# ve JavaScript projeleri için **çıkış yolu**
   - Visual Basic projeleri için **derleme çıkış yolu**
   - Visual C++ projeleri için **çıkış dizini**

   Çıkış oluşturmak için yolu yazın (kök proje dizinine mutlak veya göreli) veya bunun yerine bu klasöre gitmek için **Gözden** geçirme ' yi seçin.

   ![Visual Studio C# projesi için çıkış yolu özelliği](media/output-path.png)
   
   > [!NOTE]
   > Bazı projeler varsayılan olarak yapı yolundaki Framework ve Runtime içerir. bunu değiştirmek için **Çözüm Gezgini**' de proje düğümüne sağ tıklayın, **Project dosyayı düzenle**' yi seçin ve aşağıdakileri ekleyin:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Çıktı belirttiğiniz konuma oluşturulmadığından, Visual Studio menü çubuğunda ilgili yapılandırmayı (örneğin, **hata ayıklama** veya **Sürüm**) oluştururken emin olun.
>
> ![Visual Studio 2019 ' de derleme yapılandırma seçicisi](media/build-configuration-chooser.png)

## <a name="see-also"></a>Ayrıca bkz.

- [yapı sayfası, Project tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Genel özellik sayfası (proje)](/cpp/build/reference/general-property-page-project)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
