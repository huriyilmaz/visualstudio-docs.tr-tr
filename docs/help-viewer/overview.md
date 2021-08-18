---
title: Çevrimdışı yardım belgeleri
description: Microsoft Yardım Görüntüleyicisi kullanarak Visual Studio ve .NET gibi çeşitli ürünler ve teknolojiler için çevrimdışı yardım Microsoft Yardım Görüntüleyicisi.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 4bf24de415421f0407f0de68357e607050acdbb6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041483"
---
# <a name="microsoft-help-viewer"></a>Microsoft Yardım Görüntüleyicisi

Yerel bilgisayarınıza çeşitli ürün ve teknolojilerin içeriğini yüklemek ve görüntülemek için Microsoft Yardım Görüntüleyicisi. Bu ürünler arasında Visual Studio, .NET, dil başvurusu, SQL Server ve Windows geliştirme yer amaktadır. Yardım Görüntüleyicisi şunları sağlar:

- Kitap olarak da adlandırılan içerik kümelerini indirin. Bu, "çevrimdışı" olarak çalışmaya devam ediyorsanız ve belgelere erişiminiz varsa yararlı olabilir.

- İçindekiler tablosuna göz atarak ve bu tabloda arama yapan başlıkları başa göre bulun.

- Dizinde konuları arama.

- Tam metin arama kullanarak bilgi bulun.

- Görüntüleme, yer işareti ekleme ve yazdırma konuları.

Yardım Görüntüleyicisi'ni yüklemek için [bkz. Microsoft Yardım Görüntüleyicisi yüklemesi.](../help-viewer/installation.md) Yardım konularını çevrimiçi yerine Yardım Görüntüleyicisi'nde  okumaya başlamak için, Visual Studio menüsünde Yardım Görüntüleyicisi'nde Yardım Tercihi  >  **Başlatmayı Ayarla'ya gidin.**

> [!TIP]
> İnternet bağlantınız olmadığınız zaman görüntüley etmek için içeriği yerel olarak indirmenin bir diğer yolu da pdf sürümünü indirmektir. Dosyanın içindekiler docs.microsoft.com içindekiler (TOC) alt kısmında, ilgili İçindekiler'e ilişkin tüm makaleleri içeren bir PDF dosyasını indirmek için bir bağlantı içerir.
>
> ![Pdf'yi indirme Visual Studio belgeleri](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Yardım Görüntüleyicisi turu

Gezinti sekmelerini kullanarak, yüklü içeriği konu sekmesinde veya sekmelerde görüntüleyebilirsiniz ve İçeriği Yönet sekmesini kullanarak içeriği **yönetebilirsiniz.** Ayrıca araç çubuğundaki düğmeleri kullanarak ek görevler gerçekleştirebilir ve pencerenin sağ alt köşesinde ek bilgiler bulabilirsiniz.

### <a name="navigation-tabs"></a>Gezinti sekmeleri

|Tab|Açıklama|
|---|-----------|
|İçindekiler|Yüklü içeriği hiyerarşi (içindekiler tablosu) olarak görüntüler. Görünen başlıkları filtreleme ölçütlerini belirtabilirsiniz.|
|Dizin oluşturma|Dizinli terimlerin alfabetik listesini görüntüler. Dizinde arama yapmak, girdileri filtreleme ölçütlerini belirtmek ve dizin girişlerinin belirttiğiniz metni içermesini veya bu metinle başlamalarını gerekli kabilirsiniz.|
|Sık Kullanılanlar|Sık Kullanılanlara Ekle düğmesini seçerek konuları "sık **kullanılanlara" ekleyebilirsiniz** ve konular bu sekmede görünür. Geçmiş **bölümünde** yakın zamanda görüntüley listeniz olan konuların listesi görüntülenir.|
|Arayın|kod ve konu başlıkları dahil olmak üzere içeriğin herhangi bir yerinde terim aramanızı sağlayan bir metin kutusu sağlar.|

### <a name="view-topics"></a>Konuları görüntüleme

Her konu kendi sekmesinde görünür ve aynı anda birden çok konu açabilirsiniz.

### <a name="manage-content"></a>İçeriği yönetme

İçeriği Yönet sekmesini kullanarak içeriği yükleyebilir, güncelleştirebilirsiniz, silebilir **ve silebilirsiniz.** Sekmenin üst kısmında, bir ağ  konumdan mı yoksa bir diskten mi yoksa URI'den mi kitap yüklensin? belirtmek için Yükleme kaynağı denetimi kullanabilirsiniz. Yerel **mağaza yolu** kutusunda yerel bilgisayarda kitapların yüklü olduğu yerler görüntülenir ve Taşı düğmesini seçerek bunları farklı bir konuma **taşıyabilirsiniz.**

İçerik listesinde, hangi kitapları yükleyebilirsiniz veya zaten yüklemişsiniz, bir güncelleştirmenin mevcut olup olmadığı ve her kitabın ne kadar büyük olduğu görüntülenir. Uygun Ekle veya Kaldır bağlantılarını ve ardından  Bekleyen  değişiklikler bölmesinin altındaki Güncelleştir düğmesini seçerek bir veya **daha** fazla kitabı yükleyebilir **veya kaldırabilirsiniz.** Önceden yüklemiş olduğunuz kitaplarda güncelleştirmeler varsa pencerenin alt kısmında bulunan  Şimdi indirmek için buraya tıklayın bağlantısını seçerek bu içeriği yenileyin. Buna ek olarak, ek kitaplar yüklendiğinde güncelleştirmeler varsa tüm yüklü kitaplar yenilenir.

> [!NOTE]
> Yardım Görüntüleyicisi yöneticisi **bu özellikleri** devre dışı bıraksa veya İnternet erişimi yoksa İçeriği Yönet sekmesinin işlevselliği farklılık gösterebilir.

### <a name="toolbar-buttons"></a>Araç çubuğu düğmeleri

Yardım Görüntüleyicisi **penceresindeki araç** çubuğu aşağıdaki düğmeleri içerir:

- İçeriğinde **Konuyu Göster** düğmesi, konunun İçerikler sekmesindeki **konumunu** gösterir.

- Sık **Kullanılanlara Ekle** düğmesi etkin konuyu Sık Kullanılanlar **sekmesine** ekler.

- Konu **Başlığında Bul** düğmesi, etkin konudaki arama metnini vurgular.

- Yazdır **düğmesi** etkin konunun önizlemesini yazdırır veya gösterir.

- Görüntüleyici **Seçenekleri düğmesi,** metnin ne kadar büyük olduğu, kaç arama sonucun geri dönmesi, geçmişinde kaç konu göster olduğu ve güncelleştirmelerin çevrimiçi olarak olup olmadığı gibi ayarları görüntüler.

- İçeriği **Yönet düğmesi** İçeriği Yönet sekmesini **etkin** yapar.

- Sağ tarafta yer alan küçük üçgen, konu sekmeleri ve İçeriği Yönet sekmesi de dahil olmak üzere sekme **listesini** açar. Etkin sekme yapmak için bir sekme adı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Yardım Görüntüleyicisi yükleme](../help-viewer/installation.md)
- [Yardım Görüntüleyicisi yönetici kılavuzu](../help-viewer/administrator-guide.md)
- [Yerel içeriği yükleme ve yönetme](../help-viewer/install-manage-local-content.md)
