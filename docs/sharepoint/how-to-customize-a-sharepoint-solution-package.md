---
title: 'nasıl yapılır: SharePoint çözüm paketini özelleştirme | Microsoft Docs'
description: bir SharePoint çözüm paketi (. wsp) yapmak ve özelleştirmek için paket tasarımcısını kullanın. Paketlenmiş bildirim dosyasını görüntüleyin veya üzerine yazın. Bildirim şablonunu değiştirin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: ca3341b252f94a4415904744840f24cb05b56b56
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636897"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>nasıl yapılır: SharePoint çözüm paketini özelleştirme
  Paket Tasarımcısını bir paket (*. wsp*) oluşturmak ve özelleştirmek için kullanabilirsiniz. örneğin, SharePoint proje öğeleri ve özellikler ekleyebilir, çözüm dağıtıldığında Web sunucusunun sıfırlanıp sıfırlanmadığını belirtebilir ve dağıtım sunucusu türünü ayarlayabilirsiniz.

## <a name="open-the-package-designer"></a>Paket tasarımcısını açın

#### <a name="to-open-the-package-designer"></a>Paket tasarımcısını açmak için

- **Çözüm Gezgini**' de **paket**' e çift tıklayın veya **paket** için kısayol menüsünde **Tasarımcı görünüm** ' ü seçin.

## <a name="view-the-packaged-manifestffile"></a>Paketlenmiş manifestfFile dosyasını görüntüleme
 Paketlenmiş bildirim dosyasını değiştirmek ve oluşturmak için paket tasarımcısını kullanabilirsiniz. Ardından, bu dosya için XML kodunu Visual Studio görüntüleyebilirsiniz.

#### <a name="to-view-the-xml-source-file"></a>XML kaynak dosyasını görüntülemek için

1. **Paket tasarımcısında**, **bildirim**' ı seçin.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Çözüm Gezgini kullanarak paketlenmiş bildirim dosyasını görüntülemek için

1. **Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.

2. Paket ' i genişletin, Package. Package ' i genişletin ve *Package.Template.xml* dosyasını açın.

    > [!NOTE]
    > Paket şablonu için bildirim XML dosyasını açtığınızda, dosyalar otomatik olarak onaylanır ve Hata Listesi penceresinde görüntülenen uyarıları yoksayabilirsiniz.

## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme
 paketlenmiş bildirim dosyasının xml kodunu Visual Studio xml düzenleyicisinde veya bildirim şablonu bölmesinde değiştirebilirsiniz. XML kodunda yapılan tüm değişiklikler, paketin paketlenmiş bildirim dosyası ile birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML düzenleyicisini kullanarak bildirim şablonunu değiştirme

1. **Paket tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme SEÇENEKLERI** düğümünü genişletin ve ardından **XML Düzenleyicisi 'nde aç** bağlantısını seçin.

     XML üzerinde yapılan değişiklikler paketlenmiş bildirim dosyası ile birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim şablonu bölmesini kullanarak bildirim şablonunu değiştirme

1. **Paket tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme seçenekleri** düğümünü genişletin ve ardından bildirim şablonu bölmesinde görüntülenen xml 'yi değiştirin.

     XML üzerinde yapılan değişiklikler, **paketlenmiş bildirim bölmesinin önizlemesinde** görüntülenir.

## <a name="overwrite-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasının üzerine yaz
 Paket Tasarımcısını devre dışı bırakabilir ve *manifest.xml* dosyasını el ile oluşturabilirsiniz. Bu yordamı ilk gerçekleştirişinizde, paket Tasarımcısı 'ndaki geçerli ayarlar paket şablonu XML dosyasına kaydedilir. Ardından, XML kodunu değiştirebilir veya üzerine yazabilirsiniz.

> [!NOTE]
> paket tasarımcısı devre dışı bırakıldığında XML dosyasında SharePoint proje öğeleri ve özellikleri ekler veya kaldırırsanız, bu proje öğeleri ve özellikler paketlenmez.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Tasarımcıyı devre dışı bırakarak paketlenmiş bildirim dosyasının üzerine yazmak için

1. **Paket tasarımcısında**, **bildirim** sekmesini seçin.

2. **Düzenleme seçenekleri** düğümünü GENIŞLETIN, **XML DÜZENLEYICISI bağlantısında oluşturulan XML üzerine yaz ve bildirimi Düzenle** ' yi seçin ve ardından **Evet** düğmesini seçin.

     Şablon, geçerli paketlenmiş bildirim dosyası ile güncelleştirilir.

## <a name="enable-the-package-designer"></a>Paket Tasarımcısını etkinleştir
 *manifest.xml* dosyasını özelleştirmek Için paket tasarımcısını yeniden etkinleştirebilirsiniz.

#### <a name="to-re-enable-the-designer"></a>Tasarımcıyı yeniden etkinleştirmek için

1. **Paket tasarımcısında**, **bildirim düzenlemelerini ve tasarımcı bağlantısını yeniden etkinleştirin** ve ardından **Evet** düğmesini seçin.

     Şablon orijinal metinle yenilenir ve XML üzerinde yapılan değişiklikler kaybedilir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
