---
title: MSSCCPRJ. SCC Dosya | Microsoft Docs
description: MSSCCPRJ hakkında bilgi edinmek için. Kaynak Denetimi eklentisi tarafından kullanılan yerel ve istemci tarafı bir dosya olan SCC dosyası, Visual Studio SDK ile çalışır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899257"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC dosyası
IDE kullanarak Visual Studio denetimi altına bir çözüm veya proje yer aldığında, IDE iki önemli bilgi parçası alır. Bilgiler, kaynak denetimi eklentisinden dizeler şeklinde gelir. "AuxPath" ve "ProjName" dizeleri IDE'de opaktır, ancak eklenti tarafından sürüm denetiminde çözümü veya projeyi bulmak için kullanılır. IDE genellikle [SccGetProjPath](../extensibility/sccgetprojpath-function.md)çağırarak bu dizeleri ilk kez alır ve ardından bunları gelecekteki [SccOpenProject](../extensibility/sccopenproject-function.md)çağrıları için çözüme veya proje dosyasına kaydeder. Çözüm ve proje dosyalarına ekli olduğunda, bir kullanıcı sürüm denetiminde olan çözüm ve proje dosyalarını dallara, forklara veya kopyalarken "AuxPath" ve "ProjName" dizeleri otomatik olarak güncelleştirilmez. Çözüm ve proje dosyalarının sürüm denetiminde doğru konumlarını işaret etmek için kullanıcıların dizeleri el ile güncelleştirmeleri gerekir. Dizelerin opak olması gerektiği için, bunların nasıl güncelleştirilmiş olması gerektiği her zaman net değildir.

 Kaynak denetimi eklentisi, "AuxPath" ve "ProjName" dizelerini *MSSCCPRJ.SCC* dosyası adlı özel bir dosyada depolayarak bu sorunu önleyebilirsiniz. Eklentiye ait ve bu dosyanın bakımını yapılan yerel bir istemci tarafı dosyasıdır. Bu dosya hiçbir zaman kaynak denetimi altına yerleştirilmse de, kaynak denetimli dosyaları içeren her dizin için eklenti tarafından oluşturulur. Çözüm ve proje Visual Studio hangi dosyaların olduğunu belirlemek için, kaynak denetim eklentisi dosya uzantılarını standart veya kullanıcı tarafından sağlanan bir listeyle karşılaştırabilirsiniz. IDE, bir eklentinin *MSSCCPRJ.SCC* dosyasını desteklediğini algılayan "AuxPath" ve "ProjName" dizelerini çözüm ve proje dosyalarına eklemez ve bu dizeleri *MSSCCPRJ.SCC* dosyasından okur.

 *MSSCCPRJ.SCC* dosyasını destekleyen bir kaynak denetimi eklentisi aşağıdaki yönergelere uymalıdır:

- Dizin başına yalnızca bir *MSSCCPRJ.SCC* dosyası olabilir.

- *MsSCCPRJ.SCC* dosyası, verili bir dizinde kaynak denetimi altında olan birden çok dosya için "AuxPath" ve "ProjName" dosyalarını içerebilir.

- "AuxPath" dizesinin içinde tırnak içine alınmamalı. Çevresinde sınırlayıcı olarak tırnak işaretlerinin olması izin verilir (örneğin, boş bir dizeyi belirtmek için çift tırnak çifti kullanılabilir). *IDE, MSSCCPRJ.SCC* dosyasından okunurken "AuxPath" dizesinde yer alan tüm tırnakları alır.

- MSSCCPRJ'de "ProjName" *dizesi. SCC dosyası,* işlevden döndürülen dizeyle tam olarak `SccGetProjPath` eşleşmeli. İşlev tarafından döndürülen dizenin etrafında tırnak varsa *MSSCCPRJ.SCC* dosyasındaki dizenin tırnak içine alınarak tırnak içine alınarak veya tam tersi gerekir.

- Kaynak *denetimi altına her dosya yerleştirildiğinde MSSCCPRJ.SCC* dosyası oluşturulur veya güncelleştirilir.

- *MSSCCPRJ.SCC* dosyası silinirse, sağlayıcı bu dizinle ilgili bir kaynak denetimi işlemi gerçekleştirdiğinde dosyayı yeniden oluşturması gerekir.

- *MsSCCPRJ.SCC dosyası,* tanımlanan biçimi kesinlikle izlemeli.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ'nin çizimi. SCC dosya biçimi
 Aşağıda *MSSCCPRJ.SCC* dosya biçiminin bir örneği verilmektedir (satır numaraları yalnızca kılavuz olarak sağlanır ve dosya gövdesine dahil değildir):

- [Satır 1] `SCC = This is a Source Code Control file`

- [2. Satır]

- [Satır 3] `[TestApp.sln]`

- [Satır 4] `SCC_Aux_Path = "\\server\vss\"`

- [5. satır] `SCC_Project_Name = "$/TestApp"`

- [Satır 6]

- [Satır 7] `[TestApp.csproj]`

- [8. satır] `SCC_Aux_Path = "\\server\vss\"`

- [9. satır] `SCC_Project_Name = "$/TestApp"`

 İlk satır dosyanın amacını belirtir ve bu tür tüm dosyalar için imza olarak görev kullanır. Bu satır tüm *MSSCCPRJ.SCC dosyalarında tam olarak şu şekilde görünse* de:

 `SCC = This is a Source Code Control file`

 Aşağıdaki bölümde, köşeli ayraç içinde dosya adı ile işaretlenmiş her dosyanın ayarları ayrıntılı olarak ve ayrıntılı olarak ve ayrıntılı olarak yer almaktadır. Bu bölüm, izlenirken her dosya için yinelenir. Bu satır, bir dosya adı örneğidir, yani `[TestApp.csproj]` . IDE aşağıdaki iki satırı bekler. Ancak, tanımlanan değerlerin stilini tanımlamaz. Değişkenler ve `SCC_Aux_Path` `SCC_Project_Name` 'tir.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Bu bölümün son sınırlayıcısı yoktur. Dosyanın adı ve dosyada görünen tüm değişmez bilgiler scc.h üst bilgi dosyasında tanımlanır. Daha fazla bilgi için [bkz. Kaynak denetimi eklentisi bulmak için anahtar olarak kullanılan dizeler.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak denetim eklentilerini bulmak için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
