---
title: Yerel Yardım belgelerini yükler
description: Microsoft Yardım Görüntüleyicisi kullanarak yerel Yardım belgelerini yükleyip yönetin. Bilgisayarınızda yüklü olan yardım içeriğini ekleyin, kaldırın, güncelleştirin ve taşıyın.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3401c12e35308b07a3c1bb1884af5acda221e71d
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879105"
---
# <a name="install-and-manage-local-content"></a>Yerel içerik yükleyip yönetme

Microsoft Yardım Görüntüleyicisi kullanarak, bilgisayarınızda yüklü olan yardım içeriğini yazılım geliştirme gereksinimlerinize uyacak şekilde ekleyebilir, kaldırabilir, güncelleştirebilir ve taşıyabilirsiniz.

Yerel bilgisayarınızdaki içerikleri yönetmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Ayrıca, bir kurumsal ortamda çalışıyorsanız, sistem yöneticileri kuruluşunuz için bu kararları verebileceğinden, yerel içeriği yönetilemeyebilir. Daha fazla bilgi için [Yardım Görüntüleyici Yönetici Kılavuzu](../help-viewer/administrator-guide.md)' na bakın.

## <a name="change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirme

Varsayılan olarak, Yardım Görüntüleyicisi kaynak olarak bir Microsoft Online hizmeti kullanarak içerik yükleme. Genellikle, bir sistem yöneticisinin başka bir konumda içerik yüklediği bir kurumsal ortamda çalışmadıkça, genellikle içerik kaynağınızı değiştirmemeniz gerekir.

### <a name="to-change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirmek için

1. **Içeriği Yönet** sekmesinde, **disk** seçenek düğmesini seçin.

    > [!NOTE]
    > Yöneticinizin içerik yükleme kaynağını değiştirmesini engellediği **disk** seçeneği kullanılamaz. Daha fazla bilgi için [Yardım Görüntüleyici Yönetici Kılavuzu](../help-viewer/administrator-guide.md)' na bakın.

2. Aşağıdaki adımlardan birini uygulayın:

    - Bir *. msha* dosyasının yolunu veya bir hizmet uç noktasının URL 'sini girin.

    - Bir *. msha* dosyasına gitmek Için gözataklama (**...**) düğmesini seçin.

    - Listede en son kullanılan girişi seçin.

## <a name="download-and-install-content-locally"></a>İçeriği yerel olarak indirme ve yükleme

Yerel bilgisayarınıza içerik indirip yüklüyorsanız, internet bağlantınız olmadığında konuları görüntüleyebilirsiniz.

> [!IMPORTANT]
> İçeriği yüklemek için yönetici izinlerine sahip bir hesapla oturum açmalısınız.

> [!NOTE]
> Visual Studio IDE, Ingilizce dışındaki bir dile ayarlandıysa, Ingilizce içerik, yerelleştirilmiş içerik veya her ikisini de yükleyebilirsiniz. Ancak, yalnızca Ingilizce sürümü yüklerseniz ve **Görüntüleyici seçenekleri** iletişim kutusundaki **Tüm gezinti sekmelerine ve F1 Isteklerine Ingilizce içerik dahil et** onay kutusunu temizlerseniz içerik görünmez.

### <a name="to-download-and-install-content"></a>İçeriği indirmek ve yüklemek için

1. **Içeriği Yönet** sekmesini seçin.

2. İçerik listesinde, indirmek ve yüklemek istediğiniz kitabın veya kitapların yanındaki **Ekle** bağlantısını seçin.

     Kitap, **bekleyen değişiklikler** listesine eklenir ve belirttiğiniz kitabın veya kitapların tahmini boyutu bu listenin altında görünür. Bazı kitaplar konuları paylaştığından, birden çok kitabın Toplam indirme boyutu belirttiğiniz her kitabın boyutunu birbirine ekleme sonucundan daha küçük olabilir.

3. **Güncelleştir** düğmesini seçin.

     Belirttiğiniz kitap veya kitaplar, bilgisayarınızda zaten bulunan kitaplar için güncelleştirmeler ile birlikte yüklenir. Yükleme süreleri farklılık gösterir, ancak ilerleme durumunu durum çubuğunda görüntüleyebilirsiniz.

## <a name="remove-local-content"></a>Yerel içeriği kaldır

Bilgisayarınızdan istenmeyen içerikleri kaldırarak disk alanından tasarruf edebilirsiniz.

> [!IMPORTANT]
> İçeriği kaldırmak için yönetici izinlerinizin olması gerekir.

> [!NOTE]
> Visual Studio IDE, Ingilizce dışında bir dile ayarlanmışsa içerik görünmez, yerelleştirilmiş içeriği kaldırır ve **Görüntüleyici seçenekleri** iletişim kutusundaki **Tüm gezinti sekmesinde ve F1 Isteklerindeki Ingilizce içeriği dahil et** onay kutusunu temizlemiş olursunuz.

### <a name="to-remove-content"></a>İçeriği kaldırmak için

1. **Içeriği Yönet** sekmesini seçin.

2. İçerik listesinde, kaldırmak istediğiniz kitabın veya kitapların yanındaki **Kaldır** bağlantısını seçin.

     Kitap, **bekleyen değişiklikler** listesine eklenir.

3. **Güncelleştir** düğmesini seçin.

     Belirttiğiniz kitap veya kitaplar bilgisayarınızdan kaldırılır.

## <a name="update-local-content"></a>Yerel içeriği Güncelleştir

Durum çubuğu, yüklü içeriklerinizin güncelleştirmelerinin ne zaman kullanılabilir olduğunu gösterir.

> [!IMPORTANT]
> **Yardım Görüntüleyicisi** 'nin çevrimiçi güncelleştirmeleri otomatik olarak denetlemesini Istiyorsanız, **Görüntüleyici seçenekleri** iletişim kutusunu açmanız ve ardından **Içerik güncelleştirmelerini denetlemek için çevrimiçi ol** onay kutusunu seçmeniz gerekir.

### <a name="to-update-local-content"></a>Yerel içeriği güncelleştirmek için

- Durum çubuğunun sağ alt köşesinde, **şimdi karşıdan yüklemek için burayı tıklatın** bağlantısını seçin.

Güncelleştirme süreleri farklılık gösterebilir, ancak durum çubuğunda güncelleştirme ilerleme durumunu görüntüleyebilirsiniz.

## <a name="move-local-content"></a>Yerel içeriği taşı

Yüklü içeriği yerel bilgisayarınızdaki bir ağ paylaşımından veya yerel bilgisayarınızdaki başka bir bölüme taşıyarak disk alanından tasarruf edebilirsiniz.

> [!IMPORTANT]
> İçeriği taşımak için yönetici izinlerine sahip bir hesapla oturum açmalısınız.

### <a name="to-move-local-content"></a>Yerel içeriği taşımak için

1. **Içeriği Yönet** sekmesinde, **yerel mağaza yolu**altında **Taşı** düğmesini seçin.

     **Içeriği taşı** iletişim kutusu açılır.

2. **Metin kutusuna** içerik için farklı bir konum girin ve **Tamam** düğmesini seçin.

3. İçerik taşındığında **Kapat** düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)