---
title: Zaman uyumlu bir şekilde otomatik yüklenen uzantılar
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699380"
---
# <a name="synchronously-autoloaded-extensions"></a>Zaman uyumlu bir şekilde otomatik yüklenen uzantılar

Eşzamanlı olarak otomatik yüklenen uzantılar Visual Studio'nun performansı üzerinde olumsuz bir etkiye sahiptir ve bunun yerine eşzamanlı otomatik yükleme kullanmak üzere dönüştürülmelidir. Varsayılan olarak, Visual Studio 2019 herhangi bir uzantıdan eşzamanlı otomatik yüklenmiş paketleri engeller ve kullanıcıyı not eder.

![uzatma uyumluluk uyarısı](media/extension-compatibility-warning-16-1.png.png)

Şunları yapabilirsiniz:

- Uzantıların otomatik yüklenmesine izin vermek için **senkron otomatik yüklemeye izin** ver'i tıklatın. Visual Studio seçeneklerinde bu ayarı değiştirmek için Ortam'ı tıklatın ve ardından Uzanlar'ı tıklatın ve ardından onay kutusunu seçin "Uzantıların eşzamanlı otomatik yüklenmesine izin verin". 

- Uzantılar ve araç pencereleri ile performans sorunlarını gösteren [Performans Yöneticisi iletişim kutusunu](#performance-manager-dialog) açmak için Performansı **Yönet'i** tıklatın.

- Bildirimi kapatmak ve gelecekteki bildirimlerin varolan yüklü uzantıları engellemesi **için geçerli uzantılar için bu iletiyi gösterme'yi** tıklatın. Otomatik olarak otomatik olarak otomatik olarak yüklenen yeni bir uzantı eklerseniz, bu bildirim yeniden görüntülenir. Diğer Visual Studio özellikleri hakkında bildirimler almaya devam eceksiniz.

## <a name="performance-manager-dialog"></a>Performans Yöneticisi iletişim kutusu

![performans yöneticisi iletişim kutusu](media/performance-manager.png)

Herhangi bir kullanıcı oturumuna eşit olarak yüklenen tüm **uzantılar, Amortismana Ait API'ler** sekmesinde görünür.

* Azalan API'ler hakkında daha fazla bilgi toplamak için **bu sorun hakkında daha fazla bilgi** için tıklayın.
* Geçiş ilerlemesi için uzantı satıcılarına başvurun.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Grup ilkesini kullanarak senkron otomatik yük ayarlarını belirtin

Yöneticiler, eşzamanlı otomatik yüklemeye izin vermek için Bir Grup İlkesi'ni etkinleştirebilir. Bunu yapmak için, aşağıdaki anahtara kayıt defteri tabanlı bir ilke ayarlayın:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Giriş = **İzin Verilen**

Değer = (DWORD)
* **0** senkron otomatik yük izin verilmez
* **1** senkron otomatik yük izin verilir

## <a name="extension-authors"></a>Uzantılı yazarlar
Uzantılı yazarlar, Paketleri AsyncPackage'a geçir'de asynchronous autoload'a geçirmek [için yönergeler bulabilirler.](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)

## <a name="see-also"></a>Ayrıca bkz.
Visual Studio 2019'daki senkron otomatik yükleme ayarları hakkında daha fazla bilgi için [Senkron Otomatik Yükleme Davranışı](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) sayfasına bakın.
