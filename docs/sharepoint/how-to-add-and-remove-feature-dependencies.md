---
title: 'Nasıl: Özellik Bağımlılıkları Ekleme ve Kaldırma | Microsoft Docs'
description: Visual Studio'da Özellik Tasarımcısı'SharePoint kullanarak SharePoint çözümünüze özellik bağımlılıkları ekleme ve kaldırmayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
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
ms.openlocfilehash: d0e2a1ad31543e9248502e822c3905e274887c463cba5fe4c63c0b4c4acbb5c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425303"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Nasıl yapılanlar: Özellik bağımlılıkları ekleme ve kaldırma
  SharePoint Özelliğiniz, işlevler veya veriler için diğer Özelliklere bağlı olabilir. Böyle durumlarda, bu diğer Özellikleri Özelliğiniz için bağımlılıklar olarak işaretlebilirsiniz. Bu şekilde, SharePoint sunucusu, özelliğiniz etkinleştirilmeden önce bağımlı Özelliklerin etkinleştirilmesi sağlar.

## <a name="add-dependencies"></a>Bağımlılık ekleme
 Çözümünüze bağımlılıklar olarak başka Özellikler de eklersiniz. Bu şekilde, özelliğiniz yüklenmeden önce gerekli Özelliklerin yüklü ve etkinleştirildiğinden emin olun.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Çözümde bir özele bağımlılık eklemek için

1. Özellik Tasarımcısı'ni açın, **Özellik Etkinleştirme Bağımlılıkları düğümünü** genişletin ve ekle **düğmesini** seçin.

2. Özellik **Etkinleştirme Bağımlılıkları** Ekle iletişim kutusunda  Çözüm seçeneğinde Özelliklere bağımlılık ekle düğmesini seçin, bağımlılık olarak eklemek istediğiniz özelliğin başlığını ve ardından Ekle **düğmesini** seçin.

     **Ctrl** tuşunu seçerken birden çok başlık seçerek birden fazla özellik ebilirsiniz.

## <a name="addi-custom-dependencies"></a>Özel bağımlılıklar ekleme
 Bir SharePoint sunucusuna zaten dağıtılmış olan özellikleri bağımlılık olarak ekebilirsiniz. Bu şekilde, SharePoint tüm bağımlı Özelliklerin Özelliğiniz yüklenmeden önce etkinleştirildiğinden emin olmak için etkinleştirme işlemini denetler.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Özellik kimliğine göre bağımlılık eklemek için

1. Özellik Tasarımcısı'ni açın, **Özellik Etkinleştirme Bağımlılıkları düğümünü** genişletin ve ekle **düğmesini** seçin.

2. Özellik **Etkinleştirme Bağımlılıkları Ekle iletişim** kutusunda Özel bağımlılık **ekle seçeneğini** belirleyin.

3. Özellik **Kimliği metin** kutusuna, etkinleştirme bağımlılığı olarak işaretlemek istediğiniz Özelliğin GUID'ini girin ve ardından Ekle **düğmesini** seçin.

## <a name="edit-custom-dependencies"></a>Özel bağımlılıkları düzenleme
 Daha önce ekley istediğiniz özel bağımlılıkları düzenleyebilirsiniz. Ancak, çözümünüzde yer alan bağımlı Özellikler yalnızca kaldırılabilir, düzenlenemez.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Çözümde bir özelliğin bağımlılığını değiştirmek için

1. Özellik Tasarımcısı'ni açın ve ardından Özellik **Etkinleştirme Bağımlılıkları düğümünü** genişletin.

2. Düzenlemek istediğiniz özelliğin adını ve ardından Düzenle **düğmesini** seçin.

3. Özel **Özellik Etkinleştirme Bağımlılığını Düzenle** iletişim kutusunda başlığı, Özellik Kimliği'ni veya açıklamayı değiştir ardından Gönder **düğmesini** seçin.

## <a name="remove-dependencies"></a>Bağımlılıkları kaldırma

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Çözümde bir özele bağımlılığı kaldırmak için

1. Özellik Tasarımcısı'nda Özellik **Etkinleştirme Bağımlılıkları** düğümünü genişletin, kaldırmak istediğiniz özelliğin adını seçin ve ardından Kaldır **düğmesini** seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint oluşturma](../sharepoint/creating-sharepoint-features.md)
- [Nasıl SharePoint: SharePoint özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl kullanılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
