---
title: MSSCCPRJ. SCC Dosyası | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702462"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC dosyası
IDE'yi kullanarak bir Visual Studio çözümveya projesini kaynak denetimi altına yerleştirdiğinizde, IDE iki önemli bilgi alır. Bilgiler, dizeleri şeklindeki kaynak denetim eklentisinden gelir. "AuxPath" ve "ProjName" adlarını taşıyan bu dizeleri, IDE'ye opaktır, ancak sürüm denetiminde çözümü veya projeyi bulmak için eklenti tarafından kullanılırlar. IDE genellikle [SccGetProjPath](../extensibility/sccgetprojpath-function.md)çağırarak ilk kez bu dizeleri alır , ve daha sonra [SccOpenProject](../extensibility/sccopenproject-function.md)gelecekteki aramalar için çözüm veya proje dosyasında kaydeder. Çözüm ve proje dosyalarına katıştırıldığında, "AuxPath" ve "ProjName" dizeleri, kullanıcı sürüm denetiminde olan çözümü ve proje dosyalarını dalladığında otomatik olarak güncelleştirilmez. Çözüm ve proje dosyalarının sürüm denetiminde doğru konuma işaret ettiğinden emin olmak için, kullanıcıların dizeleri el ile güncelleştirmeleri gerekir. Dizeleri opak olması gerekiyordu olduğundan, nasıl güncellenmesi gerektiğini her zaman açık olmayabilir.

 Kaynak denetimi eklentisi, "AuxPath" ve "ProjName" dizelerini *MSSCCPR.SCC* dosyası adı verilen özel bir dosyada depolayarak bu sorunu önleyebilir. Eklenti tarafından sahip olunan ve tutulan yerel, istemci tarafı dosyasıdır. Bu dosya hiçbir zaman kaynak denetimi altına yerleştirilmese de, kaynak denetimli dosyalar içeren her dizin için eklenti tarafından oluşturulur. Hangi dosyaların Visual Studio çözümü ve proje dosyaları olduğunu belirlemek için, kaynak denetimi eklentisi dosya uzantılarını standart veya kullanıcı tarafından sağlanan bir listeyle karşılaştırabilir. IDE, bir eklentinin *MSSCCPRJ.SCC* dosyasını desteklediğini algıladıktan sonra, "AuxPath" ve "ProjName" dizelerini çözüm ve proje dosyalarına yerleştirmeyi durdurur ve bunun yerine *MSSCCPRJ.SCC* dosyasından bu dizeleri okur.

 *MSSCCPRJ.SCC* dosyasını destekleyen bir kaynak denetim eklentisi aşağıdaki yönergelere uymalıdır:

- Dizin başına yalnızca bir *MSSCCPRJ.SCC* dosyası olabilir.

- Bir *MSSCCPRJ.SCC* dosyası, belirli bir dizini içinde kaynak denetimi altında olan birden çok dosya için "AuxPath" ve "ProjName" içerebilir.

- "AuxPath" dizesi içinde tırnak içermemelidir. Etrafında delimiters olarak tırnak izin verilir (örneğin, çift tırnak bir çift boş bir dize belirtmek için kullanılabilir). IDE, *MSSCCPRJ.SCC* dosyasından okunduğunda "AuxPath" dizesinden tüm tırnakları söker.

- MSSCCPRJ'deki "ProjName" *dizesi. SCC* `SccGetProjPath` dosyası, işlevden döndürülen dizeyle tam olarak eşleşmelidir. İşlev tarafından döndürülen dize etrafında tırnak işaretleri varsa, *MSSCCPRJ.SCC* dosyasındaki dize etrafında tırnak işaretleri olmalıdır ve bunun tersi de vardır.

- Bir *MSSCCPRJ.SCC* dosyası, bir dosya kaynak denetimi ne zaman yerleştirildiğinde oluşturulur veya güncelleştirilir.

- Bir *MSSCCPRJ.SCC* dosyası silinirse, bir sağlayıcı bu dizini ile ilgili bir kaynak denetim işlemi gerçekleştirir sonraki kez yeniden gerekir.

- Bir *MSSCCPRJ.SCC* dosyası kesinlikle tanımlanan biçimi takip etmelidir.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ bir örnek. SCC dosya biçimi
 Aşağıda *MSSCCPRJ.SCC* dosya biçiminin bir örneği (satır numaraları yalnızca kılavuz olarak sağlanır ve dosya gövdesine dahil edilmemelidir):

- [Satır 1]`SCC = This is a Source Code Control file`

- [Satır 2]

- [Satır 3]`[TestApp.sln]`

- [Satır 4]`SCC_Aux_Path = "\\server\vss\"`

- [Satır 5]`SCC_Project_Name = "$/TestApp"`

- [Satır 6]

- [Satır 7]`[TestApp.csproj]`

- [Satır 8]`SCC_Aux_Path = "\\server\vss\"`

- [Satır 9]`SCC_Project_Name = "$/TestApp"`

 İlk satır, dosyanın amacını belirtir ve bu türdeki tüm dosyalar için imza görevi görehizmet eder. Bu satır tam olarak tüm *MSSCCPRJ.SCC* dosyalarında bu şekilde görünmelidir:

 `SCC = This is a Source Code Control file`

 Aşağıdaki bölüm, kare ayraçlarda dosya adı ile işaretlenmiş her dosya için ayarları ayrıntıları. İzlenen her dosya için bu bölüm yinelenir. Bu satır, bir dosya adının bir `[TestApp.csproj]`örneğidir, yani. IDE aşağıdaki iki satırı bekler. Ancak, tanımlanan değerlerin stilini tanımlamaz. Değişkenler ve `SCC_Aux_Path` `SCC_Project_Name`.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Bu bölümün sonu delimiter yoktur. Dosyanın adı ve dosyada görünen tüm literals, scc.h üstbilgi dosyasında tanımlanır. Daha fazla bilgi için kaynak [denetimi eklentisi bulmak için anahtar olarak kullanılan Dizeleri'ne](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak kontrol eklentisi bulmak için anahtar olarak kullanılan dizeleri](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
