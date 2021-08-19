---
title: Sunucu Gezgini kullanarak SharePoint bağlantılara göz atma | Microsoft Docs
description: Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız. Sunucu Gezgini düğümleri ve düğüm kısayol menü komutları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 15b47ac8286edda99ed6115f3c6eca1aa36edcbe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060277"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız
  artık **Sunucu Gezgini** yerel SharePoint bağlantılarına gidebilirsiniz. bu tekniği kullanarak, sisteminizdeki bir SharePoint sitesinin bileşenlerine gidebilirsiniz. liste tanımları ve içerik türleri gibi SharePoint site bileşenleri, **Sunucu Gezgini** ağaç görünümünde **SharePoint bağlantıları** adlı bir düğümde görüntülenir. **Sunucu Gezgini** görüntülemek için, menü çubuğunda, Sunucu Gezgini **görüntüle**' yi seçin  >  . SharePoint site bileşenlerini görüntülemenin yanı sıra, kısayol menüsündeki komutları kullanarak öğeleri kaldırabilir, özelliklerini görüntüleyebilir veya ağaç görünümünü yenileyebilirsiniz.

> [!IMPORTANT]
> bir SharePoint sitesine gitmek için, SharePoint site koleksiyonunun yöneticisi olmanız ve yerel bilgisayarın yöneticisi olarak Visual Studio çalıştırıyor olmanız gerekir. Aksi takdirde, site **Sunucu Gezgini** görüntülenir, ancak düğümünü genişletemez. Site koleksiyonunun Yöneticisi olup olmadığını doğrulamak için, siteyi bir Web tarayıcısında açın, site **eylemleri** menüsünü açın, **Site izinleri**' ni seçin ve ardından **izinler: ekip sitesi** sayfasında, Şeritteki **Yönet** grubundan **site koleksiyonu yöneticileri** komutunu seçin. Bir site koleksiyonu yöneticisiyseniz adınız metin kutusunda görünür. **Site koleksiyonu yöneticileri** komutu Şeritteki Yönet grubunda görünmezse, site koleksiyonu için yönetici değilsiniz ve site yöneticisinden uygun izinleri edinmeniz gerekir.

## <a name="server-explorer-nodes"></a>Sunucu Gezgini düğümleri
 bir SharePoint sitesinin her bileşeni, **SharePoint bağlantıları** altındaki **Sunucu Gezgini** ağaç görünümündeki bir düğüm tarafından temsil edilir. örneğin, varsayılan SharePoint siteler, SharePoint sitesinin **tartışmalar** sayfasında görüntülenen bir tartışma türünü temsil eden tartışma adlı bir içerik türü içerir. Tartışma içerik türü çeşitli alanları içerir. **Sunucu Gezgini** içinde bu alanları görüntülemek Için **ContentTypes** düğümünü ve ardından **Discussion** düğümünü genişletin. Altında gövde, tartışma konusu ve başlık gibi çeşitli alan düğümleri bulunur.

## <a name="node-shortcut-menu-commands"></a>Düğüm kısayol menü komutları
 Her düğümün, düğüme sağ tıklayıp ve ardından **SHIFT** + **F10** tuşlarını seçerek erişebileceğiniz bir kısayol menüsü vardır. Düğüm komutları şunları içerebilir:

|Komut adı|Açıklama|
|------------------|-----------------|
|Yenile|Ağaç görünümünü, düğümün en son görüntülenmesinden bu yana oluşmuş olabilecek değişiklikleri yansıtacak şekilde güncelleştirir.|
|Sil|Seçili düğümü ağaç görünümünden kaldırır. **Note:**  bu komut yalnızca **SharePoint connections** düğümü altında listelenen SharePoint bağlantılarında etkindir.|
|Özellikler|**Özellikler** penceresinde seçili düğüm için kullanılabilen özellikleri görüntüler. Özelliklerin hepsi salt okunurdur ve her düğümde ilişkili özellikler yoktur.|
|Bağlantı ekle|, taramak istediğiniz bir SharePoint sitesi belirtmenizi sağlar. **SharePoint bağlantıları** düğümünde ve alt site düğümlerinde kullanılabilir.|
|Tarayıcıda görüntüle|Seçili listeyi Web tarayıcısında görüntüler. Bu komut, listelerde **ve kitaplıklarda** bulunan **listeler** düğümü altındaki bazı listelerde kullanılabilir.|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[nasıl yapılır: SharePoint bağlantı ekleme veya kaldırma](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|yeni bir SharePoint sitesini **Sunucu Gezgini** **SharePoint bağlantıları** düğümüne eklemek için gereken adımları açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
