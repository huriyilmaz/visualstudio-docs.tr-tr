---
description: Hata ayıklayıcı Web sitesinde kod yürütmeyi durdurdu.
title: Web sitesi çalışan işlemi IIS tarafından sonlandırıldı | Microsoft Docs
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
ms.openlocfilehash: d8fce93b1bd55930b518d21921557b4ac58e8576
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074344"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Hata: Web sitesi çalışan işlemi IIS tarafından sonlandırıldı
Hata ayıklayıcı Web sitesinde kod yürütmeyi durdurdu. bu, çalışan işlemin yanıt vermeyi durdurduğunu varsaymak için Internet Information Services (ııs) hatasına neden oldu. Bu nedenle, IIS çalışan işlemini sonlandırdı.

 Hata ayıklamaya devam etmek için, IIS 'yi çalışan işlemin devam etmesine izin verecek şekilde yapılandırmanız gerekir. Bu hata iletisi, IIS 7 ' den eski olan IIS sürümleriyle birlikte görünmez.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>IIS 7 ' yi çalışan işlemin devam etmesine izin verecek şekilde yapılandırmak için

1. **Yönetimsel Araçlar** penceresini açın.

   1. **Başlat**' a ve ardından **Denetim Masası**' nı seçin.

   2. **Denetim Masası**'nda, gerekirse **Klasik görünüme geç**' i seçin ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

2. **yönetimsel araçlar** penceresinde, **Internet Information Services (ııs) yöneticisi**' ne çift tıklayın.

    IIS Yöneticisi açılır.

3. **Bağlantılar** bölmesinde, \<computer name> gerekirse düğümü genişletin.

4. Düğüm altında \<computer name> **uygulama havuzları**' na tıklayın.

5. **uygulama havuzları** listesinde, uygulamanızın çalıştığı havuzun adına sağ tıklayın ve ardından **gelişmiş Ayarlar**' ye tıklayın.

6. **gelişmiş Ayarlar** iletişim kutusunda, **işlem modeli** bölümünü bulun ve aşağıdaki eylemlerden birini gerçekleştirin:

   - **Ping etkin** ayarını **false** olarak ayarlayın.

   - **En fazla ping yanıt süresini** 90 saniyeden daha büyük bir değere ayarlayın.

     **Ping özelliğinin etkin** olarak **ayarlanması** , IIS 'nin çalışan işleminin hala çalışır durumda olup olmadığını denetlemesini durdurur ve hata ayıklama işleminizi durdurana kadar çalışan işleminin canlı kalmasını önler. **En fazla ping yanıt süresinin** büyük bir değere AYARLANMASı, IIS 'nin çalışan işlemi izlemeye devam etmesine izin verir.

7. **gelişmiş Ayarlar** iletişim kutusunu kapatmak için **tamam** ' ı tıklatın.

8. IIS Yöneticisi 'Ni ve **Yönetimsel Araçlar** penceresini kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
