---
title: Sorun giderme
description: Mac kullanıcıları için Visual Studio için sık karşılaşılan sorunlar ve çözümler.
ms.topic: troubleshooting
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: b0f10e1f70349126ab48c41efc40f982212836f1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691892"
---
# <a name="troubleshooting"></a>Sorun giderme

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Mac için Visual Studio'daki günlükleri görüntüleme

Günlükleri, aşağıda gösterildiği gibi **Yardım > Açık Günlük Dizini** menü öğesine göz atarak bulunabilir:

![Günlük dizini menü öğeni aç](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Özel durumları görüntüleme

Bir özel durum yakalandığında, bir özel durum balonu görüntülenir. Daha fazla ayrıntı görüntülemek için **Ayrıntıları Görüntüle** düğmesini seçin:

![Özel durum hakkında daha fazla ayrıntı görüntüleme](media/troubleshooting-image2.png)

Bu, özel durumla ilgili daha fazla bilgi sağlayarak **Ayrıntıları Göster** iletişim kutusunu görüntüler:

![Ayrıntılar iletişim kutusunu göster](media/troubleshooting-image3.png)

Yukarıda numaralanmış olan iletişim kutusunun önemli bölümleri aşağıda ayrıntılı olarak açıklanmıştır:

1. Gözlenen özel durum türünün tam adını gösteren özel durum türü.
2. Özel durum nesnesinin Ileti özelliğinin değerini gösteren özel durum iletisi.
3. İç özel durum ağacı görünümünde şu anda seçili özel durum için özel durum türünün tam adını gösteren İç özel durum türü.
4. İç özel durum iletisi, İç özel durum ağacı görünümünde seçili özel durum iletisi özelliğinin değerini gösterir.
5. Stacktrace görünümü. Bu bir açıklama oku ile daraltılabilir ve yığın çerçeveleri girişleri içerir.
6. Kullanıcı kodu olmayan girişler örneği.
7. Kullanıcı kodu girişleri örneği.
8. Özel durum tüm özelliklerini ve alanlarını gösteren özellikler görünümü. Bu bir açıklama ok aracılığıyla daraltılabilir.
9. İç özel durum ağacı görünümü. Bu görünümde klavye yukarı/aşağı oklarla veya fare veya izleme dörtgeni yle iç özel durumları seçin.
10. Varsayılan olarak, bu hata ayıklama ayarlarında **Hata Ayıklama proje kodu yalnızca** seçeneği ayarlanır. Bu kutuyu seçmek, kullanıcı olmayan tüm kodun yığın izinde tek bir satıra çökmesini sağlar.
11. Çıktıyı panoya `exception.ToString()` kopyalamak için bir kopyalama düğmesi.

Bu bölümlerden bazılarının yalnızca özel durum iç özel bir özel durum olduğunda görünür olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE hatalarını giderme kaynakları (Windows'ta Visual Studio)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)