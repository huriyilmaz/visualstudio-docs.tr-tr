---
title: 'Nasıl Kullanılır: Komut Satırından Sembol Dosya Konumlarını Belirt | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 604863cbef5e42b31450ea09dffa56a1a00ae992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476895"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: Komut satırından sembol dosyası konumlarını belirtme
İşlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport komut satırı aracı nın sembole (.* pdb*) profilli bileşenlerin dosyaları ve Windows sistem dosyaları. Bir bileşen derlendiğinde sembol dosyaları oluşturulur. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın. VSPerfReport sembol dosyaları için aşağıdaki konumları otomatik olarak arar:

- **/SymbolPath** seçeneğinde veya **_NT_SYMBOL_PATH** ortam değişkeninde belirtilen yollar.

- Bir bileşenin derlendiği tam yerel yol.

- Profil oluşturma verilerini içeren dizin (.* vsp* veya . *vsps*) Dosya.

  Microsoft sağlar . bir sembol sunucuda online ürünlerinin çoğu için *pdb* dosyaları. Raporlama için kullandığınız bilgisayar Internet'e bağlıysa, VSPerfReport sembol bilgilerini otomatik olarak aramak ve dosyaları yerel bir mağazaya kaydetmek için çevrimiçi sembol sunucusuna bağlanır.

  Sembol dosyalarının ve Microsoft sembol sunucusu deposunun konumunu aşağıdaki yollarla belirtebilirsiniz:

- **_NT_SYMBOL_PATH** ortamı değişkenini ayarlayın.

- **/SymbolPath** seçeneğini VSPerfReport komut satırına ekleyin.

  Bu yöntemlerin her ikisini de kullanabilirsiniz.

> [!NOTE]
> Yerel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bilgisayara yüklenmişse, Windows simge dosyalarının konumu büyük olasılıkla zaten belirtilmiştir. Daha fazla bilgi için [bkz: Windows simgesi bilgilerine başvurun.](../profiling/how-to-reference-windows-symbol-information.md) Bu konuda daha sonra açıklandığı gibi konumu ve sunucuyu kullanmak için VSPerfReport'u yapılandırmanız gerekir.

## <a name="specify-windows-symbol-files"></a>Windows simgesi dosyalarını belirtin

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusunun kullanımını yapılandırmak için

1. Gerekirse, simge dosyalarını yerel olarak depolamak için bir dizin oluşturun.

2. **_NT_SYMBOL_PATH** ortam değişkenini veya VSPerfReport /SymbolPath seçeneğini ayarlamak için aşağıdaki sözdizimini kullanın:

    `srv*<LocalStore>*https://msdl.microsoft.com/download/symbols`

    oluşturduğunuz yerel dizinin yolu nerededir. *<LocalStore>*

## <a name="specify-component-symbol-files"></a>Bileşen sembolü dosyalarını belirtin
 Profil Oluşturma Araçları arar. bileşenlerde veya profil oluşturma veri dosyasını içeren klasörde depolanan özgün konumlarında profilini çıkarmak istediğiniz bileşenlerin *pdb* dosyaları. **_NT_SYMBOL_PATH** veya **/SymbolPath** seçeneğine bir veya daha fazla yol ekleyerek arama yapmak için başka konumlar belirtebilirsiniz. Yarı-iki nokta lı ayrı yollar.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, **_NT_SYMBOL_PATH** ortamı değişkenini Windows sembol sunucusuna, yerel dizinini **c:\Symbols'a**ayarlar.

 ```cmd
  set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/download/symbols
 ```

 Aşağıdaki VSPerfReport komut satırı **/SymbolPath** seçeneğini kullanarak arama yoluna *C:\Projects\Symbols* dizinini ekler.

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:tümü**
