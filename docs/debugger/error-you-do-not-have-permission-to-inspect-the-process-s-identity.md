---
description: İşlemin kimliğini İnceleme izniniz yok.
title: İşlem kimliğini İnceleme izniniz yok &apos; | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 7ae390a94c573e25cffe3c78b2a606a20437a9a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128618"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Hata: işlemi&#39;s kimliğini İnceleme izniniz yok
İşlemin kimliğini İnceleme izniniz yok. Bunun nedeni sisteminizin yapılandırması olabilir.

 Hata ayıklayıcı, hata ayıklama için gerekli bilgiler olan işlem kimliğini incemedi. En olası neden, Terminal Hizmetleri 'nin devre dışı bırakılmasından kaynaklanıyor. Terminal Hizmetleri hizmeti varsayılan olarak etkindir. Yeniden etkinleştirmek için bu adımları izleyin.

### <a name="to-enable-terminal-services"></a>Terminal Hizmetleri 'ni etkinleştirmek için

1. **Başlat** ' a ve ardından **Denetim Masası**' nı seçin.

2. Denetim Masası 'nda, gerekirse **Klasik görünüme geç**' i seçin ve ardından **Yönetimsel Araçlar**' a çift tıklayın.

3. **Yönetimsel Araçlar** penceresinde, **Bilgisayar Yönetimi**' ne çift tıklayın.

4. Bilgisayar Yönetimi penceresinde, **Hizmetler ve uygulamalar** düğümünü genişletin.

5. **Hizmetler ve uygulamalar** altında **Hizmetler**' e tıklayın.

     Sağ bölmede hizmetlerin bir listesi görüntülenir.

6. **Hizmetler** listesinde, **Terminal Hizmetleri** ' ne sağ tıklayın ve ardından **Özellikler**' i seçin.

7. **Terminal Hizmetleri Özellikler** penceresinde **genel** sekmesine gidin ve **Başlangıç türünü** **el ile** olarak ayarlayın.

8. **Tamam**'a tıklayın.

9. Bilgisayarı yeniden başlatın.

     Bu yordam uzak masaüstünü otomatik olarak etkinleştirmez. Bilgisayarınızda uzak masaüstü 'Nü etkinleştirmek istiyorsanız, aşağıdaki ek yordamı gerçekleştirin.

### <a name="to-enable-remote-desktop"></a>Uzak Masaüstü 'Nü etkinleştirmek için

1. **Başlat** ' a tıklayın ve **ardından Bilgisayarım '** a sağ tıklayın.

2. **Özellikler**'i seçin.

     **Sistem Özellikleri** penceresi görüntülenir.

3. **Uzak** öğesine tıklayın.

4. **Uzak Masaüstü** altında, **kullanıcıların bu bilgisayara uzaktan bağlanmasına izin ver**' i seçin.

5. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
