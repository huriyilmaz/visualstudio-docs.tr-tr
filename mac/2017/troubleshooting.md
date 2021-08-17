---
title: Sorun giderme
description: Kullanıcılar için yaygın sorunlar ve Mac için Visual Studio.
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 2eb30bb0789de78d534a420c398faaa6a3c0d2dce672bcd231b41c2d85481eca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121422160"
---
# <a name="troubleshooting"></a>Sorun giderme

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Günlükleri Mac için Visual Studio

Günlükler, aşağıda gösterildiği gibi Yardım > **Günlük** Dizini Aç menü öğesine göz atarak bulunabilir:

![Günlük dizini menü öğesini açma](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Özel durumları görüntüleme

Bir özel durum yakalendiğinde bir özel durum baloncuğu görüntülenir. Diğer ayrıntıları görüntülemek için Ayrıntıları **Görüntüle düğmesini** seçin:

![Özel durum hakkında daha fazla ayrıntı görüntüleme](media/troubleshooting-image2.png)

Bu, özel **durumla** ilgili daha fazla bilgi sağlayan Ayrıntıları Göster iletişim kutusunu görüntüler:

![Ayrıntıları göster iletişim kutusu](media/troubleshooting-image3.png)

Yukarıda numaralandırarak iletişim kutusunun önemli bölümleri aşağıda ayrıntılı olarak açıklanmıştır:

1. Gözlemlenen özel durum türünün tam adını gösteren özel durum türü.
2. Özel durum nesnesinin Message özelliğinin değerini gösteren özel durum iletisi.
3. İç özel durum ağacı görünümünde seçili olan özel durum için özel durum türünün tam adını gösteren İç özel durum türü.
4. İç özel durum iletisi, İç özel durum ağacı görünümünde seçili özel durumun İleti özelliğinin değerini gösterir.
5. Stacktrace görünümü. Bu, bir açıklama oku aracılığıyla daraltılmış olabilir ve yığın çerçeveleri girişleri içerir.
6. Kullanıcı olmayan kod girişlerinin örneği.
7. Kullanıcı kodu girdileri örneği.
8. Özel durumun tüm özelliklerini ve alanlarını gösteren Özellikler görünümü. Bu, bir açıklama okuyla daraltılmış olabilir.
9. İç özel durum ağacı görünümü. Bu görünümdeki iç özel durumları klavye yukarı/aşağı okları veya fare ya da izleme defteri ile seçin.
10. Varsayılan olarak, hata ayıklayıcı ayarlarında proje **kodunda yalnızca hata ayıkla** seçeneğinin ne olduğu olarak ayarlanır. Bu kutuyu seçmek, kullanıcı olmayan tüm kodun stacktrace'te tek satıra daraltılana kadar devam edr.
11. Çıktıyı panoya kopyalamak `exception.ToString()` için bir kopyala düğmesi.

Bu bölümlerden bazılarının yalnızca özel durumun bir iç özel durumu olduğunda görünür olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [IDE hatalarını giderme kaynakları (Visual Studio Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)