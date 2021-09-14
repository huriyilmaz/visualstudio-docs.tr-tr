---
title: 'nasıl yapılır: SharePoint özelliğini özelleştirme | Microsoft Docs'
description: Visual Studio SharePoint özelliklerini özelleştirin. özellik tasarımcısı, Çözüm Gezgini veya SharePoint paket gezgini ' nde yeni bir özellik eklediğinizde açılır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636913"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>nasıl yapılır: SharePoint özelliğini özelleştirme
  Visual Studio özellik tasarımcısını kullanarak SharePoint özellikleri oluşturabilir ve özelleştirebilirsiniz. Örneğin, özellik kapsamını ayarlayabilir ve diğer özellikleri bağımlılıklar olarak ekleyebilirsiniz. varsayılan olarak, Çözüm Gezgini veya SharePoint paket gezgini ' nde yeni bir özellik eklediğinizde özellik tasarımcısı açılır.

## <a name="opening-the-feature-designer"></a>Özellik tasarımcısını açma
 özellik tasarımcısını kullanarak bir özelliğe SharePoint proje öğeleri ekleyebilir veya kaldırabilirsiniz.

#### <a name="to-open-the-feature-designer"></a>Özellik tasarımcısını açmak için

1. **Çözüm Gezgini**, **Özellikler**' i genişletin.

2. *Özellik1* öğesini çift tıklatın veya *özellik1* öğesi için kısayol menüsünü açın ve ardından **Tasarımcı görüntüle**' yi seçin.

## <a name="view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntüleme
 Özelliği için paketlenmiş bildirim dosyasını değiştirmek ve oluşturmak için özellik tasarımcısını kullanabilirsiniz (*feature.xml*). Ardından, bu dosya için XML kodunu Visual Studio görüntüleyebilirsiniz.

#### <a name="to-view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntülemek için

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Çözüm Gezgini kullanarak paketlenmiş bildirim dosyasını görüntülemek için

1. **Çözüm Gezgini**, **tüm dosyaları göster** simgesini seçin.

2. Özellikler ' i genişletin, ÖzellikAdı ' nı genişletin, FeatureName. feature öğesini genişletin ve ardından *\<FeatureName> . Template.xml* dosyasını açın.

    > [!NOTE]
    > Özellik şablonu bildirim XML dosyasını açtığınızda, dosyalar otomatik olarak onaylanır ve Hata Listesi penceresinde görüntülenen uyarılar yoksayılabilir.

## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme
 özellik bildirim dosyasının xml kodunu Visual Studio xml düzenleyicisinde veya bildirim şablonu bölmesinde değiştirebilirsiniz. XML kodunda yapılan tüm değişiklikler, özelliği için paketlenmiş bildirim dosyası ile birleştirilir. Örneğin, bir özellik özelliğini özelleştirmek için bildirim şablonunu değiştirmek isteyebilirsiniz.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML düzenleyicisini kullanarak bildirim şablonunu değiştirme

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme SEÇENEKLERI** düğümünü genişletin ve ardından **XML Düzenleyicisi 'nde aç** bağlantısını seçin.

     XML üzerinde yapılan değişiklikler paketlenmiş bildirim dosyası ile birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim şablonu bölmesini kullanarak bildirim şablonunu değiştirme

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme seçenekleri** düğümünü genişletin ve ardından bildirim şablonu bölmesinde görüntülenen xml 'yi değiştirin.

     XML üzerinde yapılan değişiklikler, **paketlenmiş bildirim bölmesinin önizlemesinde** görüntülenir.

## <a name="overwrite-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasının üzerine yaz
 Özellik tasarımcısını devre dışı bırakabilir ve *feature.xml* dosyasını el ile oluşturabilirsiniz. Bu yordamı ilk yaptığınızda, özellik tasarımcısında geçerli ayarlar özellik şablonu XML dosyasına kaydedilir. Ardından, XML kodunu değiştirebilir veya üzerine yazabilirsiniz.

> [!NOTE]
> özellik tasarımcısı devre dışı bırakıldığında XML dosyasında SharePoint proje öğeleri ekler veya kaldırırsanız, bu proje öğeleri paketlenmez.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Tasarımcıyı devre dışı bırakarak paketlenmiş bildirim dosyasının üzerine yazmak için

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin.

2. **Düzenleme seçenekleri** düğümünü GENIŞLETIN, **XML DÜZENLEYICISI bağlantısında oluşturulan XML üzerine yaz ve bildirimi Düzenle** ' yi seçin ve ardından **Evet** düğmesini seçin.

     Şablon, geçerli paketlenmiş bildirim dosyası ile güncelleştirilir.

## <a name="enable-the-feature-designer"></a>Özellik tasarımcısını etkinleştirin
 *feature.xml* dosyasını özelleştirmek Için özellik tasarımcısını yeniden etkinleştirebilirsiniz.

#### <a name="to-re-enable-the-designer"></a>Tasarımcıyı yeniden etkinleştirmek için

1. **Özellik tasarımcısında**, **atma bildirimi düzenlemelerini seçin ve tasarımcı bağlantısını yeniden etkinleştirin** ve ardından **Evet** düğmesini seçin.

2. Şablon orijinal metinle yenilenir ve XML üzerinde yapılan değişiklikler kaybedilir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
