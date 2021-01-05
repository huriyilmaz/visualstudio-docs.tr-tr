---
title: Zaman uyumlu bir şekilde otomatik yüklenen uzantılar
description: Visual Studio 2019 ' den başlayarak, zaman uyumlu olarak yüklenen paketleri herhangi bir uzantıdan engelleyen Varsayılan davranış hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 506c098f1f385ddf39c5d000f4571a8ee92c09fc
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715450"
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

Yöneticiler, zaman uyumlu bir oto yüküne izin vermek için grup ilkesi etkinleştirebilir. Bunu yapmak için, aşağıdaki anahtarda bir kayıt defteri tabanlı ilke ayarlayın:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Giriş = **Izin verildi**

Değer = (DWORD)
* **0** zaman uyumlu bir oto yüküne izin verilmiyor
* **1** zaman uyumlu bir oto yüküne izin verilir

## <a name="extension-authors"></a>Uzantı yazarları
Uzantı yazarları, [AsyncPackage 'e geçiş](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)sırasında paketlerin zaman uyumsuz olarak geçişine yönelik yönergeler bulabilir.

## <a name="see-also"></a>Ayrıca bkz.
Visual Studio 2019 ' de zaman uyumlu tekrar yükleme ayarları hakkında daha fazla bilgi için bkz. [zaman uyumlu oto yükleme davranışı](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/) sayfası.
