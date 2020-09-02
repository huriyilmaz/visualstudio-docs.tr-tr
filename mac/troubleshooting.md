---
title: Sorun giderme
description: Mac için Visual Studio kullanıcılara ilişkin yaygın sorunlar ve çözümler.
ms.topic: troubleshooting
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: b0f10e1f70349126ab48c41efc40f982212836f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67691892"
---
# <a name="troubleshooting"></a>Sorun giderme

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Mac için Visual Studio günlükleri görüntüleme

Günlükler, aşağıda gösterildiği gibi **yardım > açma günlüğü Dizin** menü öğesine göz atarak bulunabilir:

![Günlük dizini menü öğesini aç](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Özel durumları görüntüleme

Bir özel durum yakalandığında bir özel durum balonu görüntülenir. Daha fazla ayrıntı görüntülemek için **Ayrıntıları görüntüle** düğmesini seçin:

![Özel durum hakkında daha fazla ayrıntı görüntüleyin](media/troubleshooting-image2.png)

Bu, özel durumla ilgili daha fazla bilgi sağlayan **Ayrıntıları göster** iletişim kutusunu görüntüler:

![Ayrıntıları göster iletişim kutusu](media/troubleshooting-image3.png)

Bu iletişim kutusunun yukarıda numaralandırılan önemli bölümleri aşağıda ayrıntılı olarak açıklanmıştır:

1. Gözlemlenen özel durum türünün tam adını gösteren özel durum türü.
2. Özel durum nesnesinin Ileti özelliğinin değerini gösteren özel durum iletisi.
3. Iç özel durum ağacı görünümünde Şu anda seçili olan özel durum türünün tam adını gösteren Iç özel durum türü.
4. Iç özel durum iletisi, Iç özel durum ağacı görünümünde seçilen özel durumun Ileti özelliğinin değerini gösterir.
5. StackTrace görünümü. Bu, bir açıklama oku aracılığıyla daraltılabilir ve yığın çerçeveleri girdilerini içerir.
6. Kullanıcı olmayan kod girişlerinin örneği.
7. Kullanıcı kodu girişleri örneği.
8. Özel durumun tüm özelliklerini ve alanlarını gösteren Özellikler Görünümü. Bu, bir açıklama oku aracılığıyla daraltılabilir.
9. İç özel durum ağacı görünümü. Bu görünümdeki iç özel durumları klavye yukarı/aşağı okları veya fare veya tekerleksiz ile seçin.
10. Bu, varsayılan olarak, hata ayıklayıcı ayarlarında **yalnızca hata ayıklama proje kodu** seçeneği olarak ayarlanır. Bu kutunun belirlenmesi, tüm kullanıcı olmayan kodların StackTrace içinde tek bir satırda daraltılmasına olanak tanır.
11. Çıktıyı panoya kopyalamak için bir Kopyala düğmesi `exception.ToString()` .

Bu bölümlerin bazılarının yalnızca özel durumun iç özel durumu olduğunda görünür olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE hatalarında sorun giderme kaynakları (Windows üzerinde Visual Studio)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)