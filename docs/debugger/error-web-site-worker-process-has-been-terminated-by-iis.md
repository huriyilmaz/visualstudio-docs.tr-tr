---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5991bf0b14cf4952303dba599ad47e4c8fd27a9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852419"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Hata: Web sitesi çalışan işlemi IIS tarafından sonlandırıldı
Hata ayıklayıcı Web sitesinde kod yürütmeyi durdurdu. Bu, çalışan işlemin yanıt vermeyi durdurduğunu varsaymak için Internet Information Services (IIS) hatasına neden oldu. Bu nedenle, IIS çalışan işlemini sonlandırdı.

 Hata ayıklamaya devam etmek için, IIS 'yi çalışan işlemin devam etmesine izin verecek şekilde yapılandırmanız gerekir. Bu hata iletisi, IIS 7 ' den eski olan IIS sürümleriyle birlikte görünmez.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>IIS 7 ' yi çalışan işlemin devam etmesine izin verecek şekilde yapılandırmak için

1. **Yönetimsel Araçlar** penceresini açın.

   1. **Başlat**' a ve ardından **Denetim Masası**' nı seçin.

   2. **Denetim Masası**'nda, gerekirse **Klasik görünüme geç**' i seçin ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

2. **Yönetimsel Araçlar** penceresinde, **Internet Information Services (IIS) Yöneticisi**' ne çift tıklayın.

    IIS Yöneticisi açılır.

3. **Bağlantılar** bölmesinde, \<computer name> gerekirse düğümü genişletin.

4. Düğüm altında \<computer name> **uygulama havuzları**' na tıklayın.

5. **Uygulama havuzları** listesinde, uygulamanızın çalıştığı havuzun adına sağ tıklayın ve ardından **Gelişmiş ayarlar**' a tıklayın.

6. **Gelişmiş ayarlar** iletişim kutusunda, **işlem modeli** bölümünü bulun ve aşağıdaki eylemlerden birini gerçekleştirin:

   - **Ping etkin** ayarını **false**olarak ayarlayın.

   - **En fazla ping yanıt süresini** 90 saniyeden daha büyük bir değere ayarlayın.

     **Ping özelliğinin etkin** olarak **ayarlanması** , IIS 'nin çalışan işleminin hala çalışır durumda olup olmadığını denetlemesini durdurur ve hata ayıklama işleminizi durdurana kadar çalışan işleminin canlı kalmasını önler. **En fazla ping yanıt süresinin** büyük bir değere AYARLANMASı, IIS 'nin çalışan işlemi izlemeye devam etmesine izin verir.

7. **Gelişmiş ayarlar** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

8. IIS Yöneticisi 'Ni ve **Yönetimsel Araçlar** penceresini kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)