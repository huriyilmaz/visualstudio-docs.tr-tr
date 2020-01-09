---
title: Zaman uyumlu bir şekilde otomatik yüklenen uzantılar
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa26585ff4cca909a7fb7c955b351b8860436b4
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406629"
---
# <a name="synchronously-autoloaded-extensions"></a>Zaman uyumlu bir şekilde otomatik yüklenen uzantılar

Zaman uyumlu olarak yüklenen uzantılar, Visual Studio 'nun performansı üzerinde olumsuz bir etkiye sahiptir ve bunun yerine zaman uyumsuz bir oto yükü kullanacak şekilde dönüştürülmelidir. Visual Studio 2019, varsayılan olarak herhangi bir uzantıdan zaman uyumlu olarak yüklenen paketleri engeller ve kullanıcıya bildirim gönderir.

![Uzantı uyumluluk uyarısı](media/extension-compatibility-warning-16-1.png.png)

Şunları yapabilirsiniz:

- Uzantıların oto yüklemesine izin vermek için **zaman uyumlu bir oto yüküne Izin ver** ' e tıklayın. Visual Studio seçeneklerinde bu ayarı değiştirmek için, ortam ' a ve ardından Uzantılar ' a tıklayın ve ardından "uzantıların zaman uyumlu olarak yeniden yüklenmesine Izin ver" onay kutusunu seçin. 

- Uzantılara ve araç pencereleri ile ilgili performans sorunlarını gösteren [Performans Yöneticisi iletişim kutusunu](#performance-manager-dialog) açmak Için **performansı Yönet** ' e tıklayın.

- Bildirimi kapatmak ve mevcut yüklü uzantılardan gelecek bildirimleri engellemek için **geçerli uzantılar için bu iletiyi gösterme** ' ye tıklayın. Zaman uyumlu olarak tekrar yüklenen yeni bir uzantı eklerseniz, bu bildirim yeniden görüntülenir. Diğer Visual Studio özellikleri hakkında bildirim almaya devam edersiniz.

## <a name="performance-manager-dialog"></a>Performans Yöneticisi iletişim kutusu

![Performans Yöneticisi iletişim kutusu](media/performance-manager.png)

Tüm Kullanıcı oturumlarındaki paketleri eşzamanlı olarak yükleyen tüm uzantılar **kullanım dışı API 'ler** sekmesinde görünür.

* Kullanım dışı bırakılmış API 'Ler hakkında daha fazla bilgi toplamak için **Bu sorunla Ilgili daha fazla bilgi** için tıklayın.
* Geçiş ilerlemesi için uzantı satıcılarına başvurun.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Grup İlkesi kullanarak zaman uyumlu tekrar yükleme ayarlarını belirtin

Yöneticiler, zaman uyumlu bir oto yüküne izin vermek için grup ilkesi etkinleştirebilir. Bunu yapmak için aşağıdaki anahtarı kayıt defteri tabanlı bir ilke ayarlayın:

**HKEY_LOCAL_MACHINE \Software\policies\microsoft\visualstudio\synchronousoto Load**

Giriş = **Izin verildi**

Değer (DWORD) =
* **0** zaman uyumlu bir oto yüküne izin verilmiyor
* **1** zaman uyumlu bir oto yüküne izin verilir

## <a name="extension-authors"></a>Uzantı yazarları
Uzantı yazarları, [AsyncPackage 'e geçiş](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)sırasında paketlerin zaman uyumsuz olarak geçişine yönelik yönergeler bulabilir.

## <a name="see-also"></a>Ayrıca bkz.
Visual Studio 2019 ' de zaman uyumlu tekrar yükleme ayarları hakkında daha fazla bilgi için bkz. [zaman uyumlu oto yükleme davranışı](https://aka.ms/AA52xzw) sayfası.
