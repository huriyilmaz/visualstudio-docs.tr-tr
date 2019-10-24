---
title: 'Hata: işlem&#39;kimliğini İnceleme izniniz yok | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736229"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Hata: işlem&#39;kimliğini İnceleme izniniz yok
İşlemin kimliğini İnceleme izniniz yok. Bunun nedeni sisteminizin yapılandırması olabilir.

 Hata ayıklayıcı, hata ayıklama için gerekli bilgiler olan işlem kimliğini incemedi. En olası neden, Terminal Hizmetleri 'nin devre dışı bırakılmasından kaynaklanıyor. Terminal Hizmetleri hizmeti varsayılan olarak etkindir. Yeniden etkinleştirmek için bu adımları izleyin.

### <a name="to-enable-terminal-services"></a>Terminal Hizmetleri 'ni etkinleştirmek için

1. **Başlat** ' a ve ardından **Denetim Masası**' nı seçin.

2. Denetim Masası 'nda, gerekirse **Klasik görünüme geç**' i seçin ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

3. **Yönetimsel Araçlar** penceresinde, **Bilgisayar Yönetimi**' ne çift tıklayın.

4. Bilgisayar Yönetimi penceresinde, **Hizmetler ve uygulamalar** düğümünü genişletin.

5. **Hizmetler ve uygulamalar**altında **Hizmetler**' e tıklayın.

     Sağ bölmede hizmetlerin bir listesi görüntülenir.

6. **Hizmetler** listesinde, **Terminal Hizmetleri** ' ne sağ tıklayın ve ardından **Özellikler**' i seçin.

7. **Terminal Hizmetleri Özellikler** penceresinde **genel** sekmesine gidin ve **Başlangıç türünü** **el ile**olarak ayarlayın.

8. **Tamam**'a tıklayın.

9. Bilgisayarı yeniden başlatın.

     Bu yordam uzak masaüstünü otomatik olarak etkinleştirmez. Bilgisayarınızda uzak masaüstü 'Nü etkinleştirmek istiyorsanız, aşağıdaki ek yordamı gerçekleştirin.

### <a name="to-enable-remote-desktop"></a>Uzak Masaüstü 'Nü etkinleştirmek için

1. **Başlat** ' a tıklayın ve **ardından Bilgisayarım '** a sağ tıklayın.

2. **Özellikler**' i seçin.

     **Sistem Özellikleri** penceresi görüntülenir.

3. **Uzak**öğesine tıklayın.

4. **Uzak Masaüstü**altında, **kullanıcıların bu bilgisayara uzaktan bağlanmasına izin ver**' i seçin.

5. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)