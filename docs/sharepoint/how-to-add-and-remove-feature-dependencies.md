---
title: 'Nasıl yapılır: özellik bağımlılıklarını ekleme ve kaldırma | Microsoft Docs'
description: Visual Studio 'daki Özellik tasarımcısını kullanarak SharePoint çözümünüze özellik bağımlılıklarını ekleme ve kaldırma konusunu gözden geçirin.
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
ms.workload:
- office
ms.openlocfilehash: ebec7f6b1f6d777ce7b3b914ac5c1d5629190fcc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923583"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Nasıl yapılır: özellik bağımlılıklarını ekleme ve kaldırma
  SharePoint özelliğiniz, işlevsellik veya verilere yönelik diğer özelliklere bağlı olabilir. Bu gibi durumlarda, bu diğer özellikleri özelliği için bağımlılıklar olarak işaretleyebilirsiniz. Bu şekilde, SharePoint sunucusu, özelliği etkinleştirilmeden önce bağımlı özelliklerin etkinleştirilmesini sağlar.

## <a name="add-dependencies"></a>Bağımlılık Ekle
 Çözümünüzde diğer özellikleri bağımlılıklar olarak ekleyebilirsiniz. Bu şekilde, özelliği yüklenmeden önce gerekli özelliklerin yüklendiğinden ve etkinleştirildiğinden emin olabilirsiniz.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Çözümdeki bir özelliğe bağımlılık eklemek için

1. Özellik tasarımcısını açın, **özellik etkinleştirme bağımlılıkları** düğümünü genişletin ve ardından **Ekle** düğmesini seçin.

2. **Özellik etkinleştirme bağımlılıkları Ekle** iletişim kutusunda, **çözüm seçeneği Içindeki özelliklerde bağımlılık Ekle** ' yi seçin, bağımlılık olarak eklemek istediğiniz özelliğin başlığını seçin ve sonra **Ekle** düğmesini seçin.

     **CTRL** tuşunu seçerken birden çok başlık seçerek birden fazla özellik ekleyebilirsiniz.

## <a name="addi-custom-dependencies"></a>Addı özel bağımlılıkları
 Bir SharePoint sunucusuna bağımlılık olarak zaten dağıtılan özellikler ekleyebilirsiniz. Bu şekilde, SharePoint etkinleştirme işlemi, özelliği yüklenmeden önce tüm bağımlı özelliklerin etkinleştirildiğinden emin olmak için kontrol eder.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>Özellik KIMLIĞINE göre bağımlılık eklemek için

1. Özellik tasarımcısını açın, **özellik etkinleştirme bağımlılıkları** düğümünü genişletin ve ardından **Ekle** düğmesini seçin.

2. **Özellik etkinleştirme bağımlılıkları Ekle** iletişim kutusunda **Özel bağımlılık Ekle** seçenek düğmesini seçin.

3. **ÖZELLIK kimliği** metin kutusuna, etkinleştirme bağımlılığı olarak Işaretlemek ISTEDIĞINIZ özelliğin GUID 'sini girin ve sonra **Ekle** düğmesini seçin.

## <a name="edit-custom-dependencies"></a>Özel bağımlılıkları Düzenle
 Daha önce eklediğiniz özel bağımlılıkları düzenleyebilirsiniz. Ancak, çözümünüzde bulunan bağımlı özellikler yalnızca kaldırılabilir, düzenlenemez.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Çözümdeki bir özelliğin bağımlılığını değiştirmek için

1. Özellik tasarımcısını açın ve ardından **özellik etkinleştirme bağımlılıkları** düğümünü genişletin.

2. Düzenlemek istediğiniz özelliğin adını seçin ve ardından **Düzenle** düğmesini seçin.

3. **Özel özellik etkinleştirme bağımlılığını Düzenle** iletişim kutusunda başlığı, özellik kimliğini veya açıklamayı değiştirin ve ardından **Gönder** düğmesini seçin.

## <a name="remove-dependencies"></a>Bağımlılıkları kaldır

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Çözümdeki bir özelliğe bağımlılığı kaldırmak için

1. Özellik tasarımcısında, **özellik etkinleştirme bağımlılıkları** düğümünü genişletin, kaldırmak istediğiniz özelliğin adını seçin ve ardından **Kaldır** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md)
- [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl yapılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
