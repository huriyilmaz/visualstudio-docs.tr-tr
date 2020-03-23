---
title: Performans komut satırından ölçme
description: Uygulamanızdaki CPU performansını ve yönetilen bellek kullanımını komut satırından ölçün.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c109e2ae1db28f8e08ed7c34a7ee0871a6efe670
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77558125"
---
# <a name="measure-application-performance-from-the-command-line"></a>Komut satırından uygulama performansını ölçme

Komut satırı araçlarını kullanarak uygulama hakkında performans bilgileri toplayabilirsiniz.

Bu makalede açıklanan örnekte, Microsoft Not Defteri için performans bilgileri toplarsınız, ancak aynı yöntem herhangi bir işlemin profilini çıkarmak için kullanılabilir.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2019 Önizleme 3 veya sonraki sürümleri

* Komut satırı araçlarına aşinalık

## <a name="collect-performance-data"></a>Performans verilerini toplama

Visual Studio Diagnostics CLI araçlarını kullanarak profil oluşturma, profil oluşturma aracını, toplayıcı ajanlardan biriyle birlikte bir işleme ekleyerek çalışır. Profil oluşturma aracını eklediğinizde, araç durdurulana kadar profil oluşturma verilerini yakalayan ve depolayan ve bu noktada verilerin *bir .diagsession* dosyasına aktarıldığı bir tanılama oturumu başlarsınız. Daha sonra sonuçları analiz etmek için Visual Studio bu dosyayı açabilirsiniz.

1. Not Defteri'ni başlatın ve işlem kimliğini (PID) almak için Görev Yöneticisi'ni açın. Görev Yöneticisi'nde **Ayrıntılar** sekmesinde PID'yi bulun.

1. Bir komut istemi açın ve genellikle burada, koleksiyon aracısı çalıştırılabilir dizin değiştirin.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Aşağıdaki komutu yazarak *VSDiagnostics.exe'yi* başlatın.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Dahil edilmesi gereken bağımsız değişkenler şunlardır:

   * \<*id*> Toplama oturumunu tanımlar. Kimlik 1-255 arasında bir numara olmalıdır.
   * \<*pid*>, profilini istediğiniz işlemin PID, bu durumda adım 1 bulunan PID
   * \<*configFile*>, başlatmak istediğiniz toplama aracısı için yapılandırma dosyası. Daha fazla bilgi [için aracılar için Yapılandırma dosyalarına](#config_file)bakın.

1. Not Defteri'ni yeniden boyutlandırın veya bazı ilginç profil oluşturma bilgilerinin toplandıktan emin olmak için bir şey yazın.

1. Toplama oturumunu durdurun ve aşağıdaki komutu yazarak çıktıyı bir dosyaya gönderin.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Önceki komuttan dosya çıktısına gidin ve toplanan bilgileri incelemek için Visual Studio'da açın.

## <a name="agent-configuration-files"></a><a name="config_file"></a>Aracı yapılandırma dosyaları

Toplama Aracıları, ölçmeye çalıştığınız şeye bağlı olarak farklı veri türlerini toplayan değiştirilebilir bileşenlerdir.

Kolaylık sağlamak için, bu bilgileri aracı yapılandırma dosyasında depolayabilirsiniz. Yapılandırma dosyası, *.dll* ve COM CLSID adını en az içeren bir *.json* dosyasıdır. Aşağıdaki klasörde bulabileceğiniz örnek yapılandırma dosyaları aşağıda verilmiştir:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* [CPU](../profiling/cpu-usage.md) Kullanım profil oluşturma aracı için toplanan verilere karşılık gelen CpuKullanım yapılandırmaları (Taban/Yüksek/Düşük).
* DotNetObjectAlloc yapılandırmaları (Base/Low), [.NET Nesne Ayırma aracı](../profiling/dotnet-alloc-tool.md)için toplanan verilere karşılık gelir.

Taban/Düşük/Yüksek yapılandırmalar örnekleme oranına başvurur. Örneğin, Düşük 100 örnek/saniye ve Yüksek 4000 örnek/saniyedir.

*VSDiagnostics.exe* aracının bir toplama aracısıyla çalışması için, uygun aracı için hem DLL hem de COM CLSID gerekir ve aracının da ek yapılandırma seçenekleri olabilir. Yapılandırma dosyası olmayan bir aracı kullanıyorsanız, aşağıdaki komuttaki biçimi kullanın.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>İzinler

Yüksek izinler gerektiren bir uygulamanın profilini çıkarmak için, bunu yükseltilmiş bir komut isteminden yapmanız gerekir.
