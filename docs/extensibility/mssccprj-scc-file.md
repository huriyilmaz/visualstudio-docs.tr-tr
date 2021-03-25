---
title: Mssccprj. SCC dosyası | Microsoft Docs
description: MSSCCPRJ hakkında bilgi edinin. Visual Studio SDK ile birlikte çalışarak kaynak denetimi eklentisi tarafından kullanılan yerel, istemci tarafı bir dosya olan SCC dosyası.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 945d1a4d1acde0ac3fef9918123f963cf27127f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090557"
---
# <a name="mssccprjscc-file"></a>Mssccprj. SCC dosyası
IDE kullanarak bir Visual Studio çözümü veya projesi kaynak denetimi altına yerleştirdiğinizde, IDE iki önemli bilgi parçasını alır. Bilgiler, dizeler biçimindeki kaynak denetimi eklentisinden gelir. Bu dizeler, "AuxPath" ve "ProjName", IDE 'nin opaktır, ancak eklenti tarafından sürüm denetimindeki çözümü veya projeyi bulmak için kullanılır. IDE genellikle bu dizeleri, [SccGetProjPath](../extensibility/sccgetprojpath-function.md)öğesini çağırarak ilk kez alır ve ardından bunları çözüm veya proje dosyasına daha sonra [SccOpenProject](../extensibility/sccopenproject-function.md)'e çağrılar için kaydeder. Çözüm ve proje dosyalarına gömülü olduğunda, bir Kullanıcı dalı, çatallar veya kopya ve proje dosyalarını sürüm denetiminde olan bir Kullanıcı daldığında, "AuxPath" ve "ProjName" dizeleri otomatik olarak güncellenmez. Çözümün ve proje dosyalarının sürüm denetimindeki doğru konumlarına işaret ettiğinizden emin olmak için, kullanıcıların dizeleri el ile güncelleştirmesi gerekir. Dizelerin donuk olması amaçlıyordu, bu durum her zaman nasıl güncellenmeleri gerektiğini hiç temizlemeyebilir.

 Kaynak denetimi eklentisi, "AuxPath" ve "ProjName" dizelerini *Mssccprj. SCC* dosyası adlı özel bir dosyada depolayarak bu sorundan kaçınabilir. Bu, eklenti tarafından sahip olunan ve korunan yerel, istemci tarafı bir dosyadır. Bu dosya kaynak denetimine hiçbir şekilde yerleştirilmez, ancak kaynak denetimli dosyaları içeren her dizin için eklenti tarafından oluşturulmuştur. Hangi dosyaların Visual Studio çözümü ve proje dosyaları olduğunu öğrenmek için, bir kaynak denetimi eklentisi dosya uzantılarını standart veya Kullanıcı tarafından sağlanan bir listeyle karşılaştırabilirler. IDE bir eklentinin *Mssccprj. SCC* dosyasını desteklediğini algıladıktan sonra, "AuxPath" ve "ProjName" dizelerini çözüme ve proje dosyalarına eklemeyi ve bunun yerine *Mssccprj. SCC* dosyasındaki bu dizeleri okumaları gerekir.

 *Mssccprj. SCC* dosyasını destekleyen bir kaynak denetimi eklentisi aşağıdaki yönergelere uymalıdır:

- Dizin başına yalnızca bir *Mssccprj. SCC* dosyası olabilir.

- Bir *Mssccprj. SCC* dosyası, belirli bir dizin içindeki kaynak denetimi altında bulunan birden çok dosya Için "AuxPath" ve "ProjName" dosyalarını içerebilir.

- "AuxPath" dizesinin içinde tırnak işareti olmamalıdır. Sınırlayıcı olarak tırnak içine almak için izin verilir (örneğin, bir çift tırnak çifti boş bir dizeyi göstermek için kullanılabilir). IDE, *Mssccprj. SCC* dosyasından okurken "AuxPath" dizesinden tüm tırnakları çıkaracaktır.

- Mssccprj içindeki "ProjName" dizesi *. SCC dosyası* , işlevden döndürülen dize ile tam olarak eşleşmelidir `SccGetProjPath` . İşlev tarafından döndürülen dize etrafında tırnak işareti varsa, *Mssccprj. SCC* dosyasındaki dize etrafında tırnak işareti olmalıdır ve tam tersi de geçerlidir.

- Kaynak denetimi altına bir dosya yerleştirildiğinde bir *Mssccprj. SCC* dosyası oluşturulur veya güncelleştirilir.

- Bir *Mssccprj. SCC* dosyası silinirse, bir sağlayıcı bu dizinle ilgili bir kaynak denetimi işlemi gerçekleştirdiğinde bir sonraki sefer yeniden oluşturması gerekir.

- Bir *Mssccprj. SCC* dosyası, tanımlanan biçimi kesinlikle izlemelidir.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ çizimi. SCC dosya biçimi
 Aşağıda, *Mssccprj. SCC* dosya biçiminin bir örneği verilmiştir (satır numaraları yalnızca bir kılavuz olarak sağlanır ve dosya gövdesine eklenmemelidir):

- [1. satır] `SCC = This is a Source Code Control file`

- [2. satır]

- [3. satır] `[TestApp.sln]`

- [3. satır] `SCC_Aux_Path = "\\server\vss\"`

- [5. satır] `SCC_Project_Name = "$/TestApp"`

- [Satır 6]

- [Satır 7] `[TestApp.csproj]`

- [8. satır] `SCC_Aux_Path = "\\server\vss\"`

- [Satır 9] `SCC_Project_Name = "$/TestApp"`

 İlk satır dosyanın amacını belirtir ve bu türdeki tüm dosyalar için imza işlevi görür. Bu satır tüm *Mssccprj. SCC* dosyalarında tam olarak şöyle görünmelidir:

 `SCC = This is a Source Code Control file`

 Aşağıdaki bölümde, her bir dosya için, köşeli ayraçlar içinde dosya adı tarafından işaretlenen Ayrıntılar ayarları verilmiştir. Bu bölüm izlenmekte olan her dosya için yinelenir. Bu satır bir dosya adı örneğidir, yani, `[TestApp.csproj]` . IDE aşağıdaki iki satırı bekler. Ancak, tanımlanan değerlerin stilini tanımlar. Değişkenleri `SCC_Aux_Path` ve ' dir `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Bu bölüm için bitiş sınırlayıcısı yok. Dosyanın adı ve dosyada görünen tüm sabit değerler, SCC. h üstbilgi dosyasında tanımlanmıştır. Daha fazla bilgi için bkz. [kaynak denetimi eklentisini bulmak için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak denetimi eklentisini bulmak için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
