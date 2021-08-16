---
title: Yerel yardım belgelerini yükleme
description: Aşağıdaki bilgileri kullanarak yerel yardım belgelerini Microsoft Yardım Görüntüleyicisi. Bilgisayarınızda yüklü Yardım içeriğini ekleyin, kaldırın, güncelleştirin ve taşıyın.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 59ec73b408337e12c8c0d2a17c2d2e3ab78e9dbedaf6da88fc3e576a635b912c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358434"
---
# <a name="install-and-manage-local-content"></a>Yerel içeriği yükleme ve yönetme

Bu Microsoft Yardım Görüntüleyicisi, bilgisayarınızda yüklü Yardım içeriğini yazılım geliştirme ihtiyaçlarına uyacak şekilde ekleyebilir, kaldırabilir, güncelleştirebilirsiniz ve taşıyabilirsiniz.

Yerel bilgisayarınızda içeriği yönetmek için yönetici izinlerine sahip bir hesap ile oturum açabilirsiniz. Ayrıca, bir kuruluş ortamında çalışıyorsanız yerel içeriği yöneteyemebilirsiniz, çünkü sistem yöneticileri bu kararları kuruluş için verir. Daha fazla bilgi için bkz. [Yardım Görüntüleyicisi yönetici kılavuzu.](../help-viewer/administrator-guide.md)

## <a name="change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirme

Varsayılan olarak, Yardım Görüntüleyicisi kaynak olarak bir Microsoft çevrimiçi hizmetini kullanarak içerik yüklenir. Bir sistem yöneticisinin başka bir konuma içerik yüklediği bir kurumsal ortamda çalışmadıkça genellikle içerik kaynağınızı değiştirmeyebilirsiniz.

### <a name="to-change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirmek için

1. İçeriği **Yönet sekmesinde** Disk seçeneği **düğmesini** seçin.

    > [!NOTE]
    > Yöneticiniz  içerik yükleme kaynağını değiştirmenizi önlese disk seçeneği kullanılamaz. Daha fazla bilgi için bkz. [Yardım Görüntüleyicisi yönetici kılavuzu.](../help-viewer/administrator-guide.md)

2. Aşağıdaki adımlardan birini uygulayın:

    - *Bir .msha* dosyasının yolunu veya hizmet uç noktasının URL'sini girin.

    - Bir *.msha* dosyasına gitmek için Gözat (**...**) düğmesini seçin.

    - Listede, en son kullanılan girişi seçin.

## <a name="download-and-install-content-locally"></a>İçeriği yerel olarak indirme ve yükleme

İçeriği yerel bilgisayarınıza indirip yüklürsanız, İnternet bağlantınız yoksa konuları görüntüebilirsiniz.

> [!IMPORTANT]
> İçerik yüklemek için yönetici izinlerine sahip bir hesap ile oturum açabilirsiniz.

> [!NOTE]
> IDE Visual Studio İngilizce dışında bir dile ayarlanırsa İngilizce içerik, yerelleştirilmiş içerik veya her ikisini de yükleyebilirsiniz. Bununla birlikte, Görüntüleyici Seçenekleri iletişim kutusundaki yalnızca İngilizce sürümü ve tüm gezinti sekmelerinde ve  **F1** isteklerinde İngilizce içerik ekle onay kutusu temizlendiğinde hiçbir içerik görünür.

### <a name="to-download-and-install-content"></a>İçerik indirmek ve yüklemek için

1. İçeriği Yönet **sekmesini** seçin.

2. İçerik listesinde, indirmek ve **yüklemek** istediğiniz kitap veya kitapların yanındaki Ekle bağlantısını seçin.

     Kitap Bekleyen değişiklikler listesine **eklenir ve** belirttiğiniz kitap veya kitapların tahmini boyutu bu listenin altında görünür. Bazı kitaplar konu başlıklarını paylaştığından, birden çok kitabın toplam indirme boyutu, belirttiğiniz her kitabın boyutlarını bir araya eklemenin sonucundan daha küçük olabilir.

3. Güncelleştir **düğmesini** seçin.

     Belirttiğiniz kitap veya kitaplar, bilgisayarınızda zaten sahip olduğunuz kitap güncelleştirmeleriyle birlikte yüklenir. Yükleme süreleri farklılık gösterir, ancak ilerleme durumunu durum çubuğunda görüntüebilirsiniz.

## <a name="remove-local-content"></a>Yerel içeriği kaldırma

Bilgisayarınızdan istenmeyen içeriği kaldırarak disk alanı kaydedebilirsiniz.

> [!IMPORTANT]
> İçeriği kaldırmak için yönetici izinlerine sahipsiniz.

> [!NOTE]
> Visual Studio IDE İngilizce dışında bir dile ayarlanırsa, yerelleştirilmiş içeriği kaldırırsanız ve Tüm gezinti sekmesine İngilizce içerik ekle ve Görüntüleyici  Seçenekleri iletişim kutusundaki **F1** istekleri onay kutusu temizlendiğinde hiçbir içerik görünür.

### <a name="to-remove-content"></a>İçeriği kaldırmak için

1. İçeriği Yönet **sekmesini** seçin.

2. İçerik listesinde, kaldırmak **istediğiniz kitapların** veya kitapların yanındaki Kaldır bağlantısını seçin.

     Kitap Bekleyen değişiklikler **listesine** eklenir.

3. Güncelleştir **düğmesini** seçin.

     Belirttiğiniz kitap veya kitaplar bilgisayarınızdan kaldırılır.

## <a name="update-local-content"></a>Yerel içeriği güncelleştirme

Durum çubuğu, yüklü içeriğinize yapılan güncelleştirmelerin ne zaman kullanılabilir olduğunu gösterir.

> [!IMPORTANT]
> Yardım Görüntüleyicisi'nin çevrimiçi güncelleştirmeleri otomatik olarak denetlemesini görmek için Görüntüleyici Seçenekleri iletişim kutusunu açıp Çevrimiçine git'i seçerek içerik güncelleştirmelerini **denetleme onay** kutusunu seçmeniz gerekir.  

### <a name="to-update-local-content"></a>Yerel içeriği güncelleştirmek için

- Durum çubuğunun sağ alt köşesindeki Şimdi indirmek **için buraya tıklayın bağlantısını** seçin.

Güncelleştirme süreleri farklılık gösterebilir, ancak güncelleştirme ilerleme durumunu durum çubuğunda görüntüebilirsiniz.

## <a name="move-local-content"></a>Yerel içeriği taşıma

Yüklü içeriği yerel bilgisayarınızdan bir ağ paylaşımına veya yerel bilgisayarınızda başka bir bölüme hareket ettirerek disk alanı kaydedebilirsiniz.

> [!IMPORTANT]
> İçeriği taşımak için yönetici izinlerine sahip bir hesap ile oturum açabilirsiniz.

### <a name="to-move-local-content"></a>Yerel içeriği taşımak için

1. İçeriği **Yönet sekmesinde,** Yerel Mağaza **Yolu altındaki** Taşı **düğmesini seçin.**

     İçeriği **Taşı** iletişim kutusu açılır.

2. To **metin** kutusuna içerik için farklı bir konum girin ve ardından Tamam **düğmesini** seçin.

3. İçerik **taşındığında** Kapat düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)