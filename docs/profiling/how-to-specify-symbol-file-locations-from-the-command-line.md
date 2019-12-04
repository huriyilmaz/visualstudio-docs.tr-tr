---
title: 'Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b4c4230ca2539b55f57990b90ae33d1f53726dc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778732"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme
İşlev adları ve satır numaraları gibi simge bilgilerini göstermek için, VSPerfReport komut satırı aracının simgeye erişimi olması gerekir (. *pdb*) profili oluşturulmuş bileşenlerin ve Windows sistem dosyalarının dosyalarını. Sembol dosyaları bir bileşen derlendiğinde oluşturulur. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport sembol dosyaları için aşağıdaki konumları otomatik olarak arar:

- **/SymbolPath** seçeneğinde veya **_NT_SYMBOL_PATH** ortam değişkeninde belirtilen yollar.

- Bir bileşenin derlendiği tam yerel yol.

- Profil oluşturma verilerini içeren dizin (. *VSP* veya. *vsps*) dosyasýný.

  Microsoft, sağlar. bir sembol sunucusunda, ürünlerinin birçoğu için *pdb* dosyaları. Raporlama için kullandığınız bilgisayar Internet 'e bağlıysa, VSPerfReport sembol bilgilerini otomatik olarak aramak ve dosyaları yerel bir depoya kaydetmek için çevrimiçi sembol sunucusuna bağlanır.

  Sembol dosyalarının ve Microsoft sembol sunucusu deposunun konumunu aşağıdaki yollarla belirtebilirsiniz:

- **_NT_SYMBOL_PATH** ortam değişkenini ayarlayın.

- VSPerfReport komut satırına **/SymbolPath** seçeneğini ekleyin.

  Bu yöntemlerin her ikisini de kullanabilirsiniz.

> [!NOTE]
> Yerel bilgisayarda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklüyse, büyük olasılıkla Windows sembol dosyaları için bir konum belirtilmiş olmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md). Yine de bu konunun ilerleyen kısımlarında açıklandığı gibi, konum ve sunucuyu kullanmak için VSPerfReport 'ı yapılandırmanız gerekir.

## <a name="specify-windows-symbol-files"></a>Windows sembol dosyalarını belirt

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusu kullanımını yapılandırmak için

1. Gerekirse, sembol dosyalarını yerel olarak depolamak için bir dizin oluşturun.

2. **_NT_SYMBOL_PATH** ortam değişkenini veya VSPerfReport/SymbolPath seçeneğini ayarlamak için aşağıdaki sözdizimini kullanın:

    **srv\\** * *localstore* **\*http://msdl.microsoft.com/download/symbols**

    Burada *LocalStore* , oluşturduğunuz yerel dizinin yoludur.

## <a name="specify-component-symbol-files"></a>Bileşen sembol dosyalarını belirt
 Profil Oluşturma Araçları arar. içinde veya profil oluşturma veri dosyasını içeren klasörde depolanan özgün konumlarında profil uygulamak istediğiniz bileşenlerin *pdb* dosyaları. **_NT_SYMBOL_PATH** veya **/SymbolPath** seçeneğine bir veya daha fazla yol ekleyerek arama yapmak için başka konumlar belirleyebilirsiniz. Yolları noktalı virgülle ayırın.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, **_NT_SYMBOL_PATH** ortam değişkenini Windows sembol sunucusuna ve yerel dizini **c:\symbols**olarak ayarlar.

 **_NT_SYMBOL_PATH = SRV\*C:\symbols\*ayarlama http://msdl.microsoft.com/download/symbols**

 Aşağıdaki VSPerfReport komut satırı, **/SymbolPath** seçeneğini kullanarak *c:\projelersymbols* dizinini arama yoluna ekler.

 **VSPerfReport**  *MyApp* **. exe/SymbolPath: c:\projelerteksymbols/Summary: ALL**
