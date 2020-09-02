---
title: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6570b1e3c16f1935813682e2c29051c4ac7d64a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016879"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme
  Bir komut isteminde MSBuild hedeflerini kullanarak, Visual Studio 'Nun SharePoint paket dosyalarını (*. wsp*) nasıl oluşturduğunu özelleştirebilirsiniz. Örneğin, paket ara dizinini ve numaralandırılmış dosyaları belirten MSBuild öğe gruplarını değiştirmek için MSBuild özelliklerini özelleştirebilirsiniz.

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

2. Dosyayı **CustomLayout. SharePoint. targets**olarak adlandırın ve SharePoint projesinin klasörüne kaydedin.

3. Projeyi açın, kısayol menüsünü açın ve ardından **Projeyi Kaldır**' ı seçin.

4. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından * \<ProjectName> . vbproj* veya * \<ProjectName> . csproj* **Düzenle** ' **yi seçin.**

5. `Import`Proje dosyasının sonuna yakın olan satırdan sonra, aşağıdaki satırı ekleyin.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Proje dosyasını kaydedin ve kapatın.

7. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **projeyi yeniden yükle**' yi seçin.

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

5. Visual Studio 'Yu yeniden başlatın ve ardından projeyi açın.

   Projeyi yayımladığınızda, paketleme başlamadan önce BeforeLayout iletisi görünür ve paketleme bittikten sonra AfterLayout iletisi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
