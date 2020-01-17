---
title: 'Nasıl yapılır: derleme çıkış dizinini değiştirme'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114258"
---
# <a name="how-to-change-the-build-output-directory"></a>Nasıl yapılır: derleme çıkış dizinini değiştirme

Projeniz tarafından oluşturulan çıktının yapılandırma bazında (hata ayıklama, yayın veya her ikisi için) konumunu belirtebilirsiniz.

## <a name="change-the-build-output-directory"></a>Derleme çıkış dizinini değiştirme

1. Projenin özellik sayfalarını açmak için **Çözüm Gezgini** içindeki proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

2. Proje türüne göre uygun sekmeyi seçin:

   - İçin C#, **derleme** sekmesini seçin.
   - Visual Basic için **Derle** sekmesini seçin.
   - Veya C++ JavaScript için **genel** sekmesini seçin.

3. Üstteki yapılandırma açılır penceresinde çıkış dosyası konumunu değiştirmek istediğiniz yapılandırmayı (**hata ayıklama**, **yayın**veya **tüm yapılandırmalar**) seçin.

4. Sayfada, proje türüne göre farklılık gösteren&mdash;çıkış yolu girişini bulun:

   - Ve JavaScript projeleri C# için **çıkış yolu**
   - Visual Basic projeleri için **derleme çıkış yolu**
   - Görsel C++ projeler için **çıkış dizini**

   Çıkış oluşturmak için yolu yazın (kök proje dizinine mutlak veya göreli) veya bunun yerine bu klasöre gitmek için **Gözden** geçirme ' yi seçin.

   ![Visual Studio C# projesi için çıkış yolu özelliği](media/output-path.png)
   
   > [!NOTE]
   > Bazı projeler varsayılan olarak yapı yolundaki Framework ve Runtime içerir. Bunu değiştirmek için **Çözüm Gezgini**' de proje düğümüne sağ tıklayın, **Proje dosyasını Düzenle**' yi seçin ve aşağıdakileri ekleyin:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Çıktı belirttiğiniz konuma oluşturulmadığından, Visual Studio menü çubuğunda ilgili yapılandırmayı (örneğin, **hata ayıklama** veya **Sürüm**) oluştururken emin olun.
>
> ![Visual Studio 2019 ' de derleme yapılandırma Seçicisi](media/build-configuration-chooser.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme sayfası, proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Genel özellik sayfası (proje)](/cpp/build/reference/general-property-page-project)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
