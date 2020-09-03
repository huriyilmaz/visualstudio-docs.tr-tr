---
title: Mssccprj. SCC dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194223"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC Dosyası
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Visual Studio çözümü veya projesi IDE kullanılarak kaynak denetimi altına yerleştirildiğinde, IDE, dizeler biçimindeki kaynak denetimi eklentisinden iki temel bilgi parçasını alır. Bu dizeler, "AuxPath" ve "ProjName", IDE 'nin opaktır, ancak eklenti tarafından sürüm denetimindeki çözümü veya projeyi bulmak için kullanılır. IDE genellikle bu dizeleri [SccGetProjPath](../extensibility/sccgetprojpath-function.md)' i çağırarak ilk kez edinir ve ardından bunları çözüm veya proje dosyasına daha sonra [SccOpenProject](../extensibility/sccopenproject-function.md)'e çağrılar için kaydeder. Çözüm ve proje dosyalarına gömülü olduğunda, bir Kullanıcı dalı, çatallar veya kopya ve proje dosyalarını sürüm denetiminde olan bir Kullanıcı daldığında, "AuxPath" ve "ProjName" dizeleri otomatik olarak güncellenmez. Çözümün ve proje dosyalarının sürüm denetimindeki doğru konumlarına işaret ettiğinizden emin olmak için, kullanıcıların dizeleri el ile güncelleştirmesi gerekir. Dizelerin donuk olması amaçlıyordu, bu durum her zaman nasıl güncellenmeleri gerektiğini hiç temizlemeyebilir.  
  
 Kaynak denetimi eklentisi, "AuxPath" ve "ProjName" dizelerini MSSCCPRJ adlı özel bir dosyada depolayarak bu sorundan kaçınabilir. SCC dosyası. Bu, eklenti tarafından sahip olunan ve korunan yerel, istemci tarafı bir dosyadır. Bu dosya kaynak denetimine hiçbir şekilde yerleştirilmez, ancak kaynak denetimli dosyaları içeren her dizin için eklenti tarafından oluşturulmuştur. Hangi dosyaların Visual Studio çözümü ve proje dosyaları olduğunu öğrenmek için, bir kaynak denetimi eklentisi dosya uzantılarını standart veya Kullanıcı tarafından sağlanan bir listeyle karşılaştırabilirler. IDE bir eklentinin MSSCCPRJ desteklediğini algıladıktan sonra. SCC dosyası, "AuxPath" ve "ProjName" dizelerini çözüme ve proje dosyalarına eklemeyi ve bu dizeleri MSSCCPRJ 'dan okumayı sona erer. Bunun yerine SCC dosyası.  
  
 MSSCCPRJ destekleyen bir kaynak denetimi eklentisi. SCC dosyası aşağıdaki yönergelere uymalıdır:  
  
- Yalnızca bir MSSCCPRJ olabilir. Dizin başına SCC dosyası.  
  
- Bir MSSCCPRJ. SCC dosyası, belirli bir dizin içindeki kaynak denetimi altında bulunan birden çok dosya için "AuxPath" ve "ProjName" dosyalarını içerebilir.  
  
- "AuxPath" dizesinin içinde tırnak işareti olmamalıdır. Sınırlayıcı olarak tırnak içine almak için izin verilir (örneğin, bir çift tırnak çifti boş bir dizeyi göstermek için kullanılabilir). IDE, MSSCCPRJ 'dan okurken "AuxPath" dizesinden tüm tırnakları çıkaracaktır. SCC dosyası.  
  
- MSSCCPRJ içindeki "ProjName" dizesi. SCC dosyası, işlevden döndürülen dize ile tam olarak eşleşmelidir `SccGetProjPath` . İşlev tarafından döndürülen dize etrafında tırnak işareti içeriyorsa, MSSCCPRJ dize olur. SCC dosyası etrafında tırnak işareti içermeli ve tam tersi de geçerlidir.  
  
- Bir MSSCCPRJ. Kaynak denetimi altına bir dosya yerleştirildiğinde SCC dosyası oluşturulur veya güncelleştirilir.  
  
- Eğer bir MSSCCPRJ. SCC dosyası silinir, bir sağlayıcı bu dizinle ilgili bir kaynak denetimi işlemi gerçekleştirdiğinde bir sonraki sefer yeniden oluşturması gerekir.  
  
- Bir MSSCCPRJ. SCC dosyası, tanımlı biçimi kesinlikle izlemelidir.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ çizimi. SCC dosya biçimi  
 Aşağıda bir MSSCCPRJ örneği verilmiştir. SCC dosya biçimi (satır numaraları yalnızca bir kılavuz olarak sağlanır ve dosya gövdesine eklenmemelidir):  
  
 [1. satır] `SCC = This is a Source Code Control file`  
  
 [2. satır]  
  
 [3. satır] `[TestApp.sln]`  
  
 [3. satır] `SCC_Aux_Path = "\\server\vss\"`  
  
 [5. satır] `SCC_Project_Name = "$/TestApp"`  
  
 [Satır 6]  
  
 [Satır 7] `[TestApp.csproj]`  
  
 [8. satır] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Satır 9] `SCC_Project_Name = "$/TestApp"`  
  
 İlk satır dosyanın amacını belirtir ve bu türdeki tüm dosyalar için imza işlevi görür. Bu satır tamamen tüm MSSCCPRJ gibi görünmelidir. SCC dosyaları:  
  
 `SCC = This is a Source Code Control file`  
  
 Her dosya için, köşeli ayraçlar içinde dosya adı tarafından işaretlenen ayarların bir bölümü aşağıda verilmiştir. Bu bölüm izlenmekte olan her dosya için yinelenir. Bu satır bir dosya adı örneğidir, yani, `[TestApp.csproj]` . IDE aşağıdaki iki satırı bekler. Ancak, tanımlanan değerlerin stilini tanımlar. Değişkenleri `SCC_Aux_Path` ve ' dir `SCC_Project_Name` .  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Bu bölüm için bitiş sınırlayıcısı yok. Dosyanın adı ve dosyada görünen tüm sabit değerler, SCC. h üstbilgi dosyasında tanımlanmıştır. Daha fazla bilgi için bkz. [kaynak denetimi eklentisini bulmak Için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
