---
title: 'Nasıl SharePoint: SharePoint Çözüm Paketi | Microsoft Docs'
description: Paket Tasarımcısı'nda bir çözüm paketi (.wsp SharePoint yapmak ve özelleştirmek için kullanın. Paketlenmiş bildirim dosyasını görüntüleme veya üzerine yazma. Bildirim şablonunu değiştirme.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026960"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Nasıl SharePoint: SharePoint paketi özelleştirme
  Paket Tasarımcısı'nda paket oluşturmak ve özelleştirmek için kullanabilirsiniz (*.wsp*). Örneğin, proje öğeleri SharePoint özellikler ekleyebilir, çözüm dağıtıldığında Web sunucusunun sıfırlandırılacağı belirtebilirsiniz ve dağıtım sunucusu türünü ayarlayın.

## <a name="open-the-package-designer"></a>Paket Tasarımcısını açma

#### <a name="to-open-the-package-designer"></a>Paket Tasarımcısını açmak için

- Bu **Çözüm Gezgini** Paket'e çift **tıklayın** veya paket **Görünüm Tasarımcısı** menüsünden Seç'i **seçin.**

## <a name="view-the-packaged-manifestffile"></a>Paketlenmiş manifestfFile dosyasını görüntüleme
 Paketlenmiş bildirim dosyasını değiştirmek ve oluşturmak için Paket Tasarımcısı'nın kullanabilirsiniz. Ardından, bu dosyanın XML kodunu Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>XML kaynak dosyasını görüntülemek için

1. Paket **Tasarımcısı'nda Bildirim'i** **seçin.**

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Çözüm Gezgini kullanarak paketlenmiş bildirim dosyasını görüntülemek için

1. Bu **Çözüm Gezgini** Tüm Dosyaları **Göster'i seçin.**

2. Paket'i genişletin, Package.package'i genişletin ve *Package.Template.xml* açın.

    > [!NOTE]
    > Paket şablonu için bildirim XML dosyasını açsanız, dosyalar otomatik olarak doğrulanır ve Hata Listesi penceresinde görünen uyarıları yoksayabilirsiniz.

## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme
 Paketlenmiş bildirim dosyasının XML kodunu xml düzenleyicisinde veya Visual Studio dosyasında değiştirebilirsiniz. XML kodunda yapılan tüm değişiklikler paketin paketlenmiş bildirim dosyasıyla birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML Düzenleyicisi'ni kullanarak bildirim şablonunu değiştirmek için

1. Paket **Tasarımcısı'nda** Bildirim **sekmesini seçin,** Seçenekleri Düzenle düğümünü **genişletin** ve ardından XML Düzenleyicisi'nde **Aç bağlantısını** seçin.

     XML'de yapılan değişiklikler paketlenmiş bildirim dosyasıyla birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim Şablonu bölmesini kullanarak bildirim şablonunu değiştirmek için

1. Paket **Tasarımcısı'nda** Bildirim **sekmesini** seçin,  Seçenekleri Düzenle düğümünü genişletin ve bildirim şablonu bölmesinde görüntülenen XML'i ayarlayın.

     XML'de yapılan değişiklikler, **Paketlenmiş Bildirim Önizleme bölmesinde** görüntülenir.

## <a name="overwrite-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasının üzerine yazma
 Paket Tasarımcısı'nın devre dışı bırakılabilir ve *manifest.xml* oluşturabilirsiniz. Bu yordamı ilk kez gerçekleştirin, Paket Tasarımcısı'nda geçerli ayarlar paket şablonu XML dosyasına kaydedilir. Ardından XML kodunu değiştirebilir veya üzerine yazabilirsiniz.

> [!NOTE]
> Paket Tasarımcısı devre dışı SharePoint xml dosyasındaki proje öğelerini ve Özellikleri ekler veya kaldırırsanız, bu proje öğeleri ve Özellikler paketli değildir.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Tasarımcıyı devre dışı bırakarak paketlenmiş bildirim dosyasının üzerine yazmak için

1. Paket **Tasarımcısı'nda** Bildirim **sekmesini** seçin.

2. Seçenekleri **Düzenle düğümünü** genişletin, XML düzenleyicisinde **Oluşturulan XML'in** üzerine yaz ve bildirimi düzenle bağlantısını ve ardından Evet **düğmesini** seçin.

     Şablon, geçerli paketlenmiş bildirim dosyasıyla güncelleştirilir.

## <a name="enable-the-package-designer"></a>Paket Tasarımcısını Etkinleştirme
 Paket Tasarımcısı'nda yeniden etkinleştirebileceğiniz  gibi,manifest.xmlözelleştirebilirsiniz.

#### <a name="to-re-enable-the-designer"></a>Tasarımcıyı yeniden etkinleştirmek için

1. Paket **Tasarımcısı'nda** Bildirim **düzenlemelerini at'ı seçin** ve tasarımcı bağlantısını yeniden etkinleştirin ve ardından Evet **düğmesini** seçin.

     Şablon özgün metinle yenilenir ve XML'de yapılan tüm değişiklikler kaybolur.

## <a name="see-also"></a>Ayrıca bkz.
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
