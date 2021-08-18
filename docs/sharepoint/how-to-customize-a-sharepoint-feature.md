---
title: 'Nasıl SharePoint: SharePoint Özelliğini | Microsoft Docs'
description: SharePoint özellikleri Visual Studio. Çözüm Gezgini Gezgini'nde yeni bir özellik SharePoint Tasarımcı açılır.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7f4df055447221d563d4725f2a49ccb826b23002
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093040"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Nasıl SharePoint: SharePoint özelleştirme
  SharePoint Tasarımcısı'SharePoint kullanarak yeni özellikler oluşturabilir ve Visual Studio. Örneğin, Özellik kapsamını ayarlayın ve diğer Özellikleri bağımlılıklar olarak ekleyin. Varsayılan olarak, Çözüm Gezgini Veya Paket Gezgini'nde yeni bir Özellik SharePoint açılır.

## <a name="opening-the-feature-designer"></a>Özellik Tasarımcısını Açma
 Özellik Tasarımcısı'SharePoint proje öğelerini bir Özellik'e ekleyebilir veya kaldırabilirsiniz.

#### <a name="to-open-the-feature-designer"></a>Özellik Tasarımcısını açmak için

1. Bu **Çözüm Gezgini** Özellikler'i **genişletin.**

2. *Feature1* öğesini çift tıklatın veya Feature1 öğesinin kısayol menüsünü açın ve ardından *Özellik1'i* Görünüm Tasarımcısı.

## <a name="view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntüleme
 Özellik Tasarımcısı'nda Özellik ( veya ) için paketlenmiş bildirim dosyasını değiştirebilir ve *feature.xml.* Ardından, bu dosyanın XML kodunu Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntülemek için

1. Özellik **Tasarımcısı'nda** Bildirim **sekmesini** seçin.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Paket bildirim dosyasını Çözüm Gezgini kullanarak görüntülemek için

1. Bu **Çözüm Gezgini,** Tüm Dosyaları **Göster simgesini** seçin.

2. Özellikler'i genişletin, FeatureName'i genişletin, FeatureName.feature'i genişletin ve.Template.xmlaçın. *\<FeatureName>*

    > [!NOTE]
    > Özellik şablonu bildirimi XML dosyasını açsanız, dosyalar otomatik olarak doğrulanır ve Hata Listesi penceresinde görünen uyarılar yoksayılabilir.

## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme
 Xml Düzenleyicisi'nde veya Bildirim Şablonu bölmesindeKimlik bildirimi Visual Studio XML kodunu değiştirebilirsiniz. XML kodunda yapılan tüm değişiklikler Özellik için paketlenmiş bildirim dosyasıyla birleştirilir. Örneğin, bir Özellik özelliğini özelleştirmek için bildirim şablonunu değiştirmek istiyor olabilir.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML Düzenleyicisi'ni kullanarak bildirim şablonunu değiştirmek için

1. Özellik **Tasarımcısı'nda** Bildirim **sekmesini seçin,** Seçenekleri Düzenle düğümünü **genişletin** ve ardından XML Düzenleyicisi'nde **Aç bağlantısını** seçin.

     XML'de yapılan değişiklikler paketlenmiş bildirim dosyasıyla birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim Şablonu bölmesini kullanarak bildirim şablonunu değiştirmek için

1. Özellik **Tasarımcısı'nda** Bildirim **sekmesini** seçin,  Seçenekleri Düzenle düğümünü genişletin ve bildirim şablonu bölmesinde görüntülenen XML'i ayarlayın.

     XML'de yapılan değişiklikler, **Paketlenmiş Bildirim Önizleme bölmesinde** görüntülenir.

## <a name="overwrite-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasının üzerine yazma
 Özellik Tasarımcısı'nın devre dışı bırakılabilir ve *feature.xml* oluşturabilirsiniz. Bu yordamı ilk kez gerçekleştirin, Özellik Tasarımcısı'nda geçerli ayarlar Özellik şablonu XML dosyasına kaydedilir. Ardından XML kodunu değiştirebilir veya üzerine yazabilirsiniz.

> [!NOTE]
> Özellik Tasarımcısı devre dışı SharePoint xml dosyasına proje öğeleri ekler veya kaldırırsanız, bu proje öğeleri paketlanmaz.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Tasarımcıyı devre dışı bırakarak paketlenmiş bildirim dosyasının üzerine yazmak için

1. Özellik **Tasarımcısı'nda** Bildirim **sekmesini** seçin.

2. Seçenekleri **Düzenle düğümünü** genişletin, XML düzenleyicisinde **Oluşturulan XML'in** üzerine yaz ve bildirimi düzenle bağlantısını ve ardından Evet **düğmesini** seçin.

     Şablon, geçerli paketlenmiş bildirim dosyasıyla güncelleştirilir.

## <a name="enable-the-feature-designer"></a>Özellik Tasarımcısını Etkinleştirme
 Özellik Tasarımcısı'nın yeniden etkinleştirebileceğiniz  gibi,feature.xmlözelleştirebilirsiniz.

#### <a name="to-re-enable-the-designer"></a>Tasarımcıyı yeniden etkinleştirmek için

1. Özellik **Tasarımcısı'nda** Bildirim **düzenlemelerini at'ı seçin ve tasarımcı bağlantısını yeniden etkinleştirin** ve ardından Evet **düğmesini** seçin.

2. Şablon özgün metinle yenilenir ve XML'de yapılan tüm değişiklikler kaybolur.

## <a name="see-also"></a>Ayrıca bkz.
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
