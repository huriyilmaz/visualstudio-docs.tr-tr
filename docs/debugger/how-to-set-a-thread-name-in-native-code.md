---
title: Yerel kodda bir Iş parçacığı adı ayarla | Microsoft Docs
description: Visual Studio çoklu iş parçacıklı uygulama hata ayıklaması sırasında yerel kodda bir iş parçacığı adı ayarlayın. İş parçacığı adlandırması iş parçacıkları penceresinde iş parçacıklarını izlemek için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 12/17/2018
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 5707d85f02fdba038565943983a113ab10b6f2a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146907"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Nasıl Yapılır: Yerel Kodda İş Parçacığı Adı Ayarlama
Visual Studio herhangi bir sürümünde iş parçacığı adlandırması mümkündür. İş parçacığı adlandırması, çalışan bir işlemde hata ayıklarken **iş** parçacıkları penceresinde ilgilendiğiniz iş parçacıklarını tanımlamak için faydalıdır. Zaman uyumlu olarak adlandırılmış iş parçacıkları, kilitlenme bilgi döküm denetimi aracılığıyla ve çeşitli araçlar kullanılarak performans yakalamaları çözümlenirken de yararlı olabilir.

## <a name="ways-to-set-a-thread-name"></a>İş parçacığı adı ayarlama yolları

Bir iş parçacığı adı ayarlamak için iki yol vardır. İlki [Setthreaddescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) işlevi aracılığıyla yapılır. ikincisi Visual Studio hata ayıklayıcısı işleme iliştirirken belirli bir özel durum oluşturulur. Her yaklaşımın avantajları ve uyarıları vardır. kullanımı `SetThreadDescription` Windows 10, sürüm 1607 veya Windows Server 2016 başlayarak desteklenir.

_Her iki yaklaşımın de_ , çalıştıkları mekanizmaların birbirinden bağımsız olduğu mekanizmalar tarafından birlikte kullanılabileceğini belirtmekte de dikkat edin.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Kullanarak bir iş parçacığı adı ayarlama `SetThreadDescription`

Avantajlar:
* hata ayıklayıcının, setthreaddescription çağrıldığında işleme bağlı olup olmadığına bakılmaksızın, iş parçacığı adları Visual Studio hata ayıklaması sırasında görülebilir.
* İş parçacığı adları, Visual Studio bir kilitlenme dökümü yüklenirken, mordıtem hata ayıklama işlemi gerçekleştirilirken görülebilir.
* ayrıca, [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) hata ayıklayıcısı ve [Windows performans çözümleyicisi](/windows-hardware/test/wpt/windows-performance-analyzer) performans çözümleyicisi gibi diğer araçlar kullanılırken iş parçacığı adları da görünür.

Uyarılar
* iş parçacığı adları yalnızca Visual Studio 2017 sürüm 15,6 ve sonraki sürümlerde görülebilir.
* post-mordıtem bir kilitlenme bilgi döküm dosyasında hata ayıklaması yaparken, iş parçacığı adları yalnızca kilitlenme Windows 10 sürüm 1607, Windows Server 2016 veya sonraki Windows sürümleri üzerinde oluşturulduysa görülebilir.

*Örnek:*

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

programınızda bir iş parçacığı adı ayarlamak için başka bir yol da, özel olarak yapılandırılmış bir özel durum oluşturarak istenen iş parçacığı adını Visual Studio hata ayıklayıcıya iletmenin bir yoludur.

Avantajlar:
* Tüm Visual Studio sürümlerinde işe yarar.

Uyarılar
* Yalnızca hata ayıklayıcı özel durum tabanlı yöntemin kullanıldığı sırada eklenmişse işe yarar.
* Bu yöntem kullanılarak ayarlanan iş parçacığı adları, dökümler veya performans analizi araçlarında kullanılamayacak.

*Örnek:*

`SetThreadName`Aşağıda gösterilen işlev bu özel durum tabanlı yaklaşımı gösterir. İş parçacığı adının, çağrı tamamlandıktan sonra, parametre için belleğin yayınlanabilmesi için iş parçacığına otomatik olarak kopyalanacağını unutmayın `threadName` `SetThreadName` .

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
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
- [Nasıl Yapılır: Yönetilen Kodda İş Parçacığı Adı Ayarlama](../debugger/how-to-set-a-thread-name-in-managed-code.md)
