---
title: 'Nasıl yapılır: ek derlemeler ekleme ve kaldırma | Microsoft Docs'
description: SharePoint çözüm paketlerinde ek derlemeler eklemeyi ve kaldırmayı öğrenin. Ayrıca, güvenli denetimler ve sınıf kaynakları ekleyin veya silin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc672a8a0ff7edd66504b5ecbf48e622fad085ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923616"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Nasıl yapılır: ek derlemeler ekleme ve kaldırma
  Bir SharePoint paketi işlevselliği veya verileri için diğer derlemelere bağımlıysa, derlemeleri çözüm paketinize (. wsp) ekleyebilirsiniz. Bu şekilde, SharePoint sunucusu özel derlemelerin bir paket ile yüklendiğinden emin olmanızı sağlar.

 Ayrıca Derlemelerle ilişkili güvenli denetimleri ve sınıf kaynak dosyalarını ekleyebilir ve değiştirebilirsiniz.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Ek derlemeler, güvenli denetimler ve sınıf kaynakları ekleyin
 SharePoint çözüm paketine ek derlemeler ekleyebilirsiniz. Korumalı bir çözümdeki ek derlemeler genel derleme önbelleğine dağıtılır, ancak korumalı bir çözümdeki SharePoint proje öğeleri içerik veritabanına eklenir. Ayrıca, bu ek derlemelere güvenli denetimler ve sınıf kaynakları da ekleyebilirsiniz. Güvenli denetimler hakkında daha fazla bilgi için bkz. [Proje Öğelerinde Paketleme ve dağıtım bilgileri sağlama](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) veya [SharePoint Foundation 'da Web bölümleri dağıtma](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))bölümünde "SafeControl girdisi oluşturma".

#### <a name="to-add-an-existing-assembly"></a>Varolan bir derlemeyi eklemek için

1. **Paket Tasarımcısını** açın. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. **Gelişmiş** sekmesini seçin.

3. **Ekle** düğmesini seçin ve ardından listeden **mevcut derlemeyi Ekle** ' yi seçin.

     **Varolan derlemeyi Ekle** iletişim kutusu görüntülenir.

4. Üç nokta (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) seçin ve ardından eklemek istediğiniz derlemeyi seçin. Taşınabilirlik amacıyla seçili derlemeye göreli bir yol kullanmanızı öneririz.

5. **Dağıtım hedefi** için, derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmak üzere **GlobalAssemblyCache** seçenek düğmesini seçin veya derlemeyi SharePoint çalıştıran sunucudaki WebApplication klasörüne dağıtmak için **WebApplication** seçenek düğmesini seçin.

#### <a name="to-add-an-assembly-from-project-output"></a>Proje çıktısından bir derleme eklemek için

1. **Paket Tasarımcısını** açın.

     Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. **Gelişmiş** sekmesini seçin.

3. **Ekle** düğmesini seçin ve ardından listeden **Proje çıktısından derleme Ekle** ' yi seçin.

     **Proje çıktısından derleme Ekle** iletişim kutusu görünür.

4. **Kaynak proje** listesinde, eklemek istediğiniz kaynak projeyi seçin.

5. **Dağıtım hedefi** için, derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtmak üzere **GlobalAssemblyCache** seçenek düğmesini seçin veya derlemeyi SharePoint çalıştıran sunucudaki WebApplication klasörüne dağıtmak için **WebApplication** seçenek düğmesini seçin.

#### <a name="to-add-a-safe-control"></a>Güvenli denetim eklemek için

1. **Varolan derlemeyi Düzenle** iletişim kutusunu açın. Bunu gerçekleştirmek için, paket tasarımcısını açın, **Gelişmiş** sekmesini seçin, bir derleme seçin ve ardından **Düzenle** düğmesini seçin.

2. **Güvenli denetimler** bölmesinde, **Yeni öğe eklemek Için buraya tıklayın ' ı** seçin.

3. **Derleme adı** sütununda, derlemenin adını girin.

4. **Ad alanı** sütununda, güvenli denetim için ad alanının adını girin.

5. **Tür adı** sütununda, türün adını girin.

#### <a name="to-add-a-class-resource"></a>Bir sınıf kaynağı eklemek için

1. **Varolan derlemeyi Düzenle** iletişim kutusunu açın. Bunu gerçekleştirmek için, paket tasarımcısını açın, **Gelişmiş** sekmesini seçin, bir derleme seçin ve ardından **Düzenle** düğmesini seçin.

2. **Sınıf kaynakları** bölmesinde, **Yeni öğe eklemek Için buraya tıklayın ' ı** seçin.

3. **Dosya adı** sütununda üç noktayı (![ASP.net Mobile Designer elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer elips")) seçin ve eklemek istediğiniz sınıf kaynağını seçin.

## <a name="delete-custom-assemblies"></a>Özel derlemeleri Sil
 Bir SharePoint paketinden derlemeleri silebilir veya var olan derlemelerden güvenli denetimleri ve sınıf kaynaklarını silebilirsiniz.

#### <a name="to-delete-an-existing-assembly"></a>Varolan bir derlemeyi silmek için

1. **Paket Tasarımcısını** açın. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. **Gelişmiş** sekmesini seçin.

3. **Ek derlemeler** bölmesinde, silmek istediğiniz özel derlemeyi seçin.

4. **Sil** düğmesini seçin.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Bir derlemeye yönelik güvenli denetimi silmek için

1. **Varolan derlemeyi Düzenle** iletişim kutusunu açın. Bunu gerçekleştirmek için, paket tasarımcısını açın, **Gelişmiş** sekmesini seçin, bir derleme seçin ve ardından **Düzenle** düğmesini seçin.

2. Silmek istediğiniz güvenli denetimi seçin.

3. Silme anahtarını seçin.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Bir derlemenin sınıf kaynağını silmek için

1. **Varolan derlemeyi Düzenle** iletişim kutusunu açın. Bunu gerçekleştirmek için, paket tasarımcısını açın, **Gelişmiş** sekmesini seçin, bir derleme seçin ve ardından **Düzenle** düğmesini seçin.

2. Silmek istediğiniz sınıf kaynağını seçin.

3. Silme anahtarını seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md)
- [Nasıl yapılır: Bir SharePoint Özelliğini Özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl yapılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
