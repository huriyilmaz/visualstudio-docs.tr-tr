---
title: 'Nasıl yapılır: yerel kodda Iş parçacığı adı ayarlama | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1f9df52bee88722006c21c28e88a2e32113942e4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732753"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Nasıl Yapılır: Yerel Kodda İş Parçacığı Adı Ayarlama
Visual Studio 'nun herhangi bir sürümünde iş parçacığı adlandırması mümkündür. İş parçacığı adlandırması, çalışan bir işlemde hata ayıklarken **iş** parçacıkları penceresinde ilgilendiğiniz iş parçacıklarını tanımlamak için faydalıdır. Zaman uyumlu olarak adlandırılmış iş parçacıkları, kilitlenme bilgi döküm denetimi aracılığıyla ve çeşitli araçlar kullanılarak performans yakalamaları çözümlenirken de yararlı olabilir.

## <a name="ways-to-set-a-thread-name"></a>İş parçacığı adı ayarlama yolları

Bir iş parçacığı adı ayarlamak için iki yol vardır. İlki [Setthreaddescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) işlevi aracılığıyla yapılır. İkincisi, Visual Studio hata ayıklayıcısı işleme iliştirirken belirli bir özel durum oluşturulur. Her yaklaşımın avantajları ve uyarıları vardır. @No__t_0 kullanımı, Windows 10, sürüm 1607 veya Windows Server 2016 ' den başlayarak desteklenir.

_Her iki yaklaşımın de_ , çalıştıkları mekanizmaların birbirinden bağımsız olduğu mekanizmalar tarafından birlikte kullanılabileceğini belirtmekte de dikkat edin.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>@No__t_0 kullanarak bir iş parçacığı adı ayarlama

Larından
* Hata ayıklayıcının, SetThreadDescription çağrıldığında işleme bağlı olup olmadığına bakılmaksızın, Visual Studio 'da hata ayıklarken iş parçacığı adları görünür.
* İş parçacığı adları, Visual Studio 'da bir kilitlenme dökümü yüklenirken, post-mordıtem hata ayıklama işlemi gerçekleştirilirken görülebilir.
* Ayrıca, [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) hata ayıklayıcısı ve [Windows Performans Çözümleyicisi](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) Performans Çözümleyicisi gibi diğer araçlar kullanılırken iş parçacığı adları da görünür.

Uyarılar
* İş parçacığı adları yalnızca Visual Studio 2017 sürüm 15,6 ve sonraki sürümlerinde görülebilir.
* Post-mordıtem bir kilitlenme bilgi döküm dosyasında hata ayıklaması yaparken, iş parçacığı adları yalnızca kilitlenme Windows 10 sürüm 1607, Windows Server 2016 veya Windows 'un sonraki sürümlerinde oluşturulduysa görülebilir.

*Örneğinde*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Özel durum oluşturarak iş parçacığı adı ayarlama

Programınızda bir iş parçacığı adı ayarlamaya yönelik başka bir yol da, özel olarak yapılandırılmış bir özel durum oluşturarak istenen iş parçacığı adını Visual Studio hata ayıklayıcısıyla iletmenin bir yoludur.

Larından
* Tüm Visual Studio sürümlerinde çalışmaktadır.

Uyarılar
* Yalnızca hata ayıklayıcı özel durum tabanlı yöntemin kullanıldığı sırada eklenmişse işe yarar.
* Bu yöntem kullanılarak ayarlanan iş parçacığı adları, dökümler veya performans analizi araçlarında kullanılamayacak.

*Örneğinde*

Aşağıda gösterilen `SetThreadName` işlevi bu özel durum tabanlı yaklaşımı gösterir. İş parçacığı adının, `SetThreadName` çağrısı tamamlandıktan sonra `threadName` parametresi için belleğin yayınlanabilmesi için iş parçacığına otomatik olarak kopyalanacağını unutmayın.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Çok İş Parçacıklı Uygulamaların Hatalarını Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Nasıl Yapılır: Yönetilen Kodda İş Parçacığı Adı Ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md)
