---
title: Komut satırından sembol dosyası konumlarını belirtme
description: VSPerfReport komut satırı aracının, işlev adları ve satır numaraları gibi sembol bilgilerini görüntülemesi için sembol (. pdb) dosyalarına erişim gerektirip gerektirmediğini öğrenin.
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
ms.openlocfilehash: e30a8d39f21c43c49f81529e94d570e016f365ec43a3944f6c8261468fc5b863
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121301037"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: Komut satırından sembol dosyası konumlarını belirtme
İşlev adları ve satır numaraları gibi simge bilgilerini göstermek için, VSPerfReport komut satırı aracının simgeye erişimi olması gerekir (.*pdb*) profili oluşturulan bileşenlerin ve Windows sistem dosyalarının dosyalarını. Sembol dosyaları bir bileşen derlendiğinde oluşturulur. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport sembol dosyaları için aşağıdaki konumları otomatik olarak arar:

- **/SymbolPath** seçeneğinde veya **_NT_SYMBOL_PATH** ortam değişkeninde belirtilen yollar.

- Bir bileşenin derlendiği tam yerel yol.

- Profil oluşturma verilerini içeren dizin (.*VSP* veya. *vsps*) dosyasýný.

  Microsoft, sağlar. bir sembol sunucusunda, ürünlerinin birçoğu için *pdb* dosyaları. Raporlama için kullandığınız bilgisayar Internet 'e bağlıysa, VSPerfReport sembol bilgilerini otomatik olarak aramak ve dosyaları yerel bir depoya kaydetmek için çevrimiçi sembol sunucusuna bağlanır.

  Sembol dosyalarının ve Microsoft sembol sunucusu deposunun konumunu aşağıdaki yollarla belirtebilirsiniz:

- **_NT_SYMBOL_PATH** ortam değişkenini ayarlayın.

- VSPerfReport komut satırına **/SymbolPath** seçeneğini ekleyin.

  Bu yöntemlerin her ikisini de kullanabilirsiniz.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]yerel bilgisayarda yüklüyse, büyük olasılıkla Windows sembol dosyaları için bir konum belirtilmiş olabilir. daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md). Yine de bu konunun ilerleyen kısımlarında açıklandığı gibi, konum ve sunucuyu kullanmak için VSPerfReport 'ı yapılandırmanız gerekir.

## <a name="specify-windows-symbol-files"></a>Windows sembol dosyalarını belirtme

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusunun kullanımını yapılandırmak için

1. Gerekirse, sembol dosyalarını yerel olarak depolamak için bir dizin oluşturun.

2. **_NT_SYMBOL_PATH** ortam değişkenini veya VSPerfReport/SymbolPath seçeneğini ayarlamak için aşağıdaki sözdizimini kullanın:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    Burada *<LocalStore>* , oluşturduğunuz yerel dizinin yoludur.

## <a name="specify-component-symbol-files"></a>Bileşen sembol dosyalarını belirt
 Profil Oluşturma Araçları arar. içinde veya profil oluşturma veri dosyasını içeren klasörde depolanan özgün konumlarında profil uygulamak istediğiniz bileşenlerin *pdb* dosyaları. **_NT_SYMBOL_PATH** veya **/SymbolPath** seçeneğine bir veya daha fazla yol ekleyerek arama yapmak için başka konumlar belirleyebilirsiniz. Yolları noktalı virgülle ayırın.

## <a name="example"></a>Örnek
 aşağıdaki komut satırı, **_NT_SYMBOL_PATH** ortam değişkenini Windows SYMBOL sunucusuna ve yerel dizinini **c:\symbols** olarak ayarlar.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Aşağıdaki VSPerfReport komut satırı, **/SymbolPath** seçeneğini kullanarak *c:\projelersymbols* dizinini arama yoluna ekler.

 **VSPerfReport**  *MyApp* **.exe/SymbolPath: c:\projelersymbols/Summary: ALL**
