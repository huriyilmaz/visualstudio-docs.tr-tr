---
title: 'Nasıl yapılır: bir SharePoint özelliğini özelleştirme | Microsoft Docs'
description: Visual Studio 'da SharePoint özelliklerini özelleştirin. Özellik Tasarımcısı, Çözüm Gezgini veya SharePoint paket Gezgini ' nde yeni bir özellik eklediğinizde açılır.
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
ms.workload:
- office
ms.openlocfilehash: 0604b6497920e1e6df0a792ce758519f425ac155
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959954"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Nasıl yapılır: bir SharePoint özelliğini özelleştirme
  Visual Studio 'daki Özellik tasarımcısını kullanarak SharePoint özelliklerini oluşturabilir ve özelleştirebilirsiniz. Örneğin, özellik kapsamını ayarlayabilir ve diğer özellikleri bağımlılıklar olarak ekleyebilirsiniz. Varsayılan olarak, Çözüm Gezgini veya SharePoint paket Gezgini ' nde yeni bir özellik eklediğinizde özellik Tasarımcısı açılır.

## <a name="opening-the-feature-designer"></a>Özellik tasarımcısını açma
 Özellik tasarımcısını kullanarak bir özelliğe SharePoint proje öğeleri ekleyebilir veya kaldırabilirsiniz.

#### <a name="to-open-the-feature-designer"></a>Özellik tasarımcısını açmak için

1. **Çözüm Gezgini**, **Özellikler**' i genişletin.

2. *Özellik1* öğesini çift tıklatın veya *özellik1* öğesi için kısayol menüsünü açın ve ardından **Tasarımcı görüntüle**' yi seçin.

## <a name="view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntüleme
 Özelliği için paketlenmiş bildirim dosyasını değiştirmek ve oluşturmak için özellik tasarımcısını kullanabilirsiniz (*feature.xml*). Daha sonra, bu dosyanın XML kodunu Visual Studio 'da görüntüleyebilirsiniz.

#### <a name="to-view-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasını görüntülemek için

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Çözüm Gezgini kullanarak paketlenmiş bildirim dosyasını görüntülemek için

1. **Çözüm Gezgini**, **tüm dosyaları göster** simgesini seçin.

2. Özellikler ' i genişletin, ÖzellikAdı ' nı genişletin, FeatureName. feature öğesini genişletin ve *\<FeatureName>.Template.xml* dosyasını açın.

    > [!NOTE]
    > Özellik şablonu bildirim XML dosyasını açtığınızda, dosyalar otomatik olarak onaylanır ve Hata Listesi penceresinde görüntülenen uyarılar yoksayılabilir.

## <a name="change-the-manifest-template"></a>Bildirim şablonunu değiştirme
 Visual Studio XML düzenleyicisinde veya bildirim şablonu bölmesinde Özellik bildirim dosyasının XML kodunu değiştirebilirsiniz. XML kodunda yapılan tüm değişiklikler, özelliği için paketlenmiş bildirim dosyası ile birleştirilir. Örneğin, bir özellik özelliğini özelleştirmek için bildirim şablonunu değiştirmek isteyebilirsiniz.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML düzenleyicisini kullanarak bildirim şablonunu değiştirme

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme SEÇENEKLERI** düğümünü genişletin ve ardından **XML Düzenleyicisi 'nde aç** bağlantısını seçin.

     XML üzerinde yapılan değişiklikler paketlenmiş bildirim dosyası ile birleştirilir.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Bildirim şablonu bölmesini kullanarak bildirim şablonunu değiştirme

1. **Özellik tasarımcısında**, **bildirim** sekmesini seçin, **düzenleme seçenekleri** düğümünü genişletin ve ardından bildirim şablonu bölmesinde görüntülenen xml 'yi değiştirin.

     XML üzerinde yapılan değişiklikler, **paketlenmiş bildirim bölmesinin önizlemesinde** görüntülenir.

## <a name="overwrite-the-packaged-manifest-file"></a>Paketlenmiş bildirim dosyasının üzerine yaz
 Özellik tasarımcısını devre dışı bırakabilir ve *feature.xml* dosyasını el ile oluşturabilirsiniz. Bu yordamı ilk yaptığınızda, özellik tasarımcısında geçerli ayarlar özellik şablonu XML dosyasına kaydedilir. Ardından, XML kodunu değiştirebilir veya üzerine yazabilirsiniz.

> [!NOTE]
> Özellik Tasarımcısı devre dışı bırakıldığında XML dosyasına SharePoint proje öğeleri ekler veya kaldırırsanız, bu proje öğeleri paketlenmez.

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
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
