---
description: Hata ayıklayıcısı Web sitesinde kodun yürütülmesini durdurdu.
title: Web sitesi çalışan işlemi IIS sunucusu tarafından | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22de4f1ef153ba2d4cda8b2663b3bfbf83ea4dd2db4db1f91b7b3679a6e6905c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263770"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Hata: Web sitesi çalışan işlemi IIS tarafından sonlandırıldı
Hata ayıklayıcısı Web sitesinde kodun yürütülmesini durdurdu. Bu durum Internet Information Services (IIS) çalışan işleminin yanıt vermenin durdurulmuş olduğunu varsaymalarına neden oldu. Bu nedenle IIS çalışan işlemini sonlandırıldı.

 Hata ayıklamaya devam etmek için IIS'yi çalışan işleminin devam edecek şekilde yapılandırmanız gerekir. Bu hata iletisi IIS 7'den eski IIS sürümleriyle birlikte görünmez.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Çalışan işleminin devamsına izin verecek şekilde IIS 7'yi yapılandırmak için

1. Yönetimsel **Araçlar penceresini** açın.

   1. **Başlat'a** tıklayın ve ardından öğesini **Denetim Masası.**

   2. Bu **Denetim Masası,** Gerekirse **Klasik Görünüme Geç'i** seçin ve ardından Yönetimsel Araçlar'a **çift tıklayın.**

2. Yönetimsel **Araçlar penceresinde,** Internet Information Services **(IIS) Yöneticisi'ne çift tıklayın.**

    IIS Yöneticisi açılır.

3. Bağlantılar **bölmesinde** gerekirse düğümü \<computer name> genişletin.

4. Düğümün \<computer name> altında Uygulama **Havuzları'ne tıklayın.**

5. Uygulama **Havuzları listesinde,** uygulamanın içinde çalıştır olduğu havuzun adına sağ tıklayın ve ardından Gelişmiş **Havuzlar'a Ayarlar.**

6. Gelişmiş **Ayarlar** iletişim kutusunda İşlem Modeli **bölümünü** bulun ve aşağıdaki eylemlerden birini gerçekleştirin:

   - Ping **Etkin'i** False olarak **ayarlayın.**

   - Ping **Maksimum Yanıt Süresi değerini** 90 saniyeden büyük bir değere ayarlayın.

     Ping **Etkin ayarının** **False** olarak etkinleştirilmesi IIS'nin çalışan işleminin hala çalışır durumda olup olmadığını denetlemeyi durdurur ve siz hata ayıklama işleminizi durdurana kadar çalışan işlemini canlı tutar. Ping **Maksimum Yanıt Süresi'ni büyük** bir değere ayarlama IIS'nin çalışan işlemini izlemeye devam ettiğine olanak sağlar.

7. **Tamam'a** tıklar ve **Gelişmiş Ayarlar** kutusunu kapatın.

8. IIS Yöneticisi'ni ve **Yönetimsel Araçlar penceresini** kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
