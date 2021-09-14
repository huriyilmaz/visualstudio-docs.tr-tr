---
title: Komut satırına simge dosyası konumlarını belirtme
description: VSPerfReport komut satırı aracının işlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için sembol (.pdb) dosyalarına erişmeyi nasıl gerektirdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5f1978ba849840ffe8177c51e054b43a3978514d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635718"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: Komut satırından sembol dosyası konumlarını belirtme
İşlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport komut satırı aracının simgesine () erişmesi gerekir.*pdb*) dosyaları ve sistem dosyalarının Windows dosyaları. Bir bileşen derlenmiş olduğunda sembol dosyaları oluşturulur. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport, sembol dosyalarını otomatik olarak aşağıdaki konumlarda arar:

- **/SymbolPath seçeneğinde veya** ortam değişkensinde **_NT_SYMBOL_PATH** yollar.

- Bileşenin derlenmiş olduğu tam yerel yol.

- Profil oluşturma verilerini içeren dizin ( .*vsp* veya . *vsps*) Dosya.

  Microsoft, sağlar. bir sembol sunucusunda çevrimiçi olan birçok ürün için *pdb* dosyaları. Raporlama için kullanmakta olduğu bilgisayar İnternet'e bağlı ise VSPerfReport, sembol bilgilerini otomatik olarak araması ve dosyaları yerel bir depoya kaydetmesi için çevrimiçi sembol sunucusuna bağlanır.

  Sembol dosyalarının ve Microsoft sembol sunucusu deposun konumunu aşağıdaki yollarla belirtebilirsiniz:

- Ortam **_NT_SYMBOL_PATH** ayarlayın.

- VSPerfReport komut satırına **/SymbolPath** seçeneğini ekleyin.

  Bu yöntemlerin ikisini de kullanabilirsiniz.

> [!NOTE]
> Yerel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bilgisayarda yüklüyse, simge dosyalarının Windows zaten belirtilmiştir. Daha fazla bilgi için, [bkz. Nasıl Windows simgesi bilgileri.](../profiling/how-to-reference-windows-symbol-information.md) VsPerfReport'un konumu ve sunucuyu bu konunun devamlarında açıklandığı gibi kullanmak üzere yapılandırmaya devam edebilirsiniz.

## <a name="specify-windows-symbol-files"></a>Simge Windows dosyaları belirtme

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusunun kullanımını yapılandırmak için

1. Gerekirse sembol dosyalarını yerel olarak depolamak için bir dizin oluşturun.

2. _NT_SYMBOL_PATH ortam değişkenlerini **veya** VSPerfReport /SymbolPath seçeneğini ayarlamak için aşağıdaki sözdizimini kullanın:

    `srv*{LocalStore}*https://msdl.microsoft.com/download/symbols`

    Burada *{LocalStore},* oluşturduğunuz yerel dizinin yoludur.

## <a name="specify-component-symbol-files"></a>Bileşen sembol dosyalarını belirtme
 Profil Oluşturma Araçları için arama. *bileşenlerde* veya profil oluşturma veri dosyasını içeren klasörde depolanan özgün konumlarında profil oluşturmak istediğiniz bileşenlerin pdb dosyaları. Arama yapmak için bir veya daha fazla yol ekleyerek veya /SymbolPath **_NT_SYMBOL_PATH** başka **konumlar belirtebilirsiniz.** Yolları noktalı virgülle ayırma.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, **_NT_SYMBOL_PATH** ortam değişkenlerini Windows ve yerel dizini **C:\Symbols olarak ayarlar.**

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Aşağıdaki VSPerfReport komut **satırı, /SymbolPath** seçeneğini kullanarak *C:\Projects\Symbols* dizinini arama yoluna ekler.

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**
