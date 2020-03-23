---
title: 'Nasıl yapilir: Yapı çıktı dizini değiştirme'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114258"
---
# <a name="how-to-change-the-build-output-directory"></a>Nasıl yapilir: Yapı çıktı dizini değiştirme

Projeniz tarafından oluşturulan çıktının konumunu yapılandırma başına olarak (hata ayıklama, sürüm veya her ikisi için) belirtebilirsiniz.

## <a name="change-the-build-output-directory"></a>Derleme çıkış dizinini değiştirme

1. Projenin özellik sayfalarını açmak için **Solution Explorer'daki** proje düğümüne sağ tıklayın ve **Özellikler'i**seçin.

2. Proje türünüze göre uygun sekmeyi seçin:

   - C# için **Yapı** sekmesini seçin.
   - Visual Basic için **Derle** sekmesini seçin.
   - C++ veya JavaScript için **Genel** sekmesini seçin.

3. Üstteki yapılandırma açılır ayında, değiştirmek istediğiniz çıktı dosyası konumunu **(Hata Ayıklama,** **Serbest Bırakma**veya **Tüm Yapılandırmalar)** yapılandırmayı seçin.

4. Proje türünüze bağlı olarak&mdash;farklı olduğu sayfada çıktı yolu girişini bulun:

   - C# ve JavaScript projeleri için **çıkış yolu**
   - Visual Basic projeleri için **çıktı yolu oluşturma**
   - Visual C++ projeleri için **çıktı dizini**

   Çıktı oluşturmak için yolu yazın (mutlak veya kök proje dizinine göre) veya bunun yerine bu klasöre göz atmak için **Gözat'ı** seçin.

   ![Visual Studio C# projesi için çıkış yolu özelliği](media/output-path.png)
   
   > [!NOTE]
   > Bazı projeler varsayılan olarak yapı yolunda çerçeve ve çalışma süresi içerir. Bunu değiştirmek **için, Çözüm Gezgini'ndeki**proje düğümüne sağ tıklayın, **Proje Dosyasını Edit'i**seçin ve aşağıdakileri ekleyin:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Çıktı belirttiğiniz konuma oluşturulmuyorsa, Visual Studio'nun menü çubuğunda seçerek ilgili yapılandırmayı (örneğin Hata **Ayıklama** veya **Sürüm)** oluşturduğunuzdan emin olun.
>
> ![Visual Studio 2019'da yapılandırma seçici oluşturun](media/build-configuration-chooser.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Genel Mülkiyet sayfası (proje)](/cpp/build/reference/general-property-page-project)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
