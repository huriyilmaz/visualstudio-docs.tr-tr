---
title: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme
titleSuffix: ''
description: bir komut isteminde MSBuild hedeflerini kullanarak Visual Studio SharePoint çözüm paketi dosyalarını (. wsp) nasıl oluşturduğunu özelleştirin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 998bcd8ca191e5d7f5c3868836b4c498cae563c2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636902"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme
  komut isteminde MSBuild hedeflerini kullanarak, Visual Studio SharePoint paket dosyalarını (*. wsp*) nasıl oluşturduğunu özelleştirebilirsiniz. örneğin, paketleme ara dizinini ve numaralandırılmış dosyaları belirten MSBuild öğesi gruplarını değiştirmek için MSBuild özelliklerini özelleştirebilirsiniz.

## <a name="customize-and-run-msbuild-targets"></a>MSBuild hedeflerini özelleştirme ve çalıştırma
 BeforeLayout ve AfterLayout hedeflerini özelleştirirseniz, paketlenecek dosyaları ekleme, kaldırma veya değiştirme gibi paket düzeninden önce görevleri gerçekleştirebilirsiniz.

#### <a name="to-customize-the-beforelayout-target"></a>BeforeLayout hedefini özelleştirmek için

1. Not Defteri gibi bir düzenleyici açın ve aşağıdaki kodu ekleyin.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Bu örnek, bu hedefin paketlemeden önce bir ileti görüntüler.

2. dosyayı **customlayout. SharePoint. targets** olarak adlandırın ve SharePoint projesi klasörüne kaydedin.

3. Projeyi açın, kısayol menüsünü açın ve ardından **Project kaldır**' ı seçin.

4. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından *\<ProjectName> . vbproj* veya *\<ProjectName> . csproj* **Düzenle** ' **yi seçin.**

5. `Import`Proje dosyasının sonuna yakın olan satırdan sonra, aşağıdaki satırı ekleyin.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Proje dosyasını kaydedin ve kapatın.

7. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Project yeniden yükle**' yi seçin.

   Projeyi yayımladığınızda, ambalaj başlamadan önce çıktıda ileti görüntülenir.

#### <a name="to-customize-the-afterlayout-target"></a>AfterLayout hedefini özelleştirmek için

1. Menü çubuğunda **Dosya**  >  **Aç**  >  **Dosya**' yı seçin.

2. **Dosya Aç** iletişim kutusunda proje klasörüne gidin, CustomLayout. Target dosyasını seçin ve ardından **Aç** düğmesini seçin.

3. Etiketinden hemen önce `</Project>` aşağıdaki kodu ekleyin:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Bu örnek, bu hedef paketlendikten sonra bir ileti görüntüler.

4. Hedefler dosyasını kaydedin ve kapatın.

5. Visual Studio yeniden başlatın ve ardından projeyi açın.

   Projeyi yayımladığınızda, paketleme başlamadan önce BeforeLayout iletisi görünür ve paketleme bittikten sonra AfterLayout iletisi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
