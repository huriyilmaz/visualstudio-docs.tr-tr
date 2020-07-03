---
title: Windows komut dosyası motorları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27a500f9df91738e2db563f7e37ee646925b674e
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835699"
---
# <a name="windows-script-engines"></a>Windows Komut Dosyası Motorları
Bir Microsoft Windows betik altyapısı uygulamak için aşağıdaki arabirimleri destekleyen bir OLE COM nesnesi oluşturun.  
  
|||  
|-|-|  
|Arabirim|Description|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Temel komut dosyası özelliğini sağlar. Bu arabirimin uygulanması gereklidir.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Betik metni ekleme, ifadeleri değerlendirme vb. olanakları sağlar. Bu arabirimin uygulanması isteğe bağlıdır; Ancak, uygulanmadığından, betik altyapısının bir betiği yüklemek için IPersist * arabirimlerinden birini uygulaması gerekir.|  
|IPersist *|Kalıcılık desteği sağlar. [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) uygulanmadığından aşağıdaki arabirimlerden en az birini uygulamanız gerekir.<br /><br /> IPersistStorage: Nesne etiketinde DATA = {URL} özniteliği için destek sağlar.<br /><br /> Ipersiststreaminit: `IPersistStorage` Nesne etiketinde, ve Data = "String-Encoded byte stream" özniteliği için de destek sağlar.<br /><br /> IPersistPropertyBag: Nesne etiketinde PARAM = özniteliği için destek sağlar.|  
  
> [!NOTE]
> Betik altyapısının bir betik durumunu kaydetme veya geri yükleme sırasında hiçbir şekilde çağrılmayacağı olasıdır `IPersist*` . Bunun yerine, boş bir betik oluşturmak için [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) çağırarak [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) kullanılır, ardından Scriptını 'lar eklenir ve [IActiveScriptParse:: AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) ve genel kod Ile olaylara bağlanır [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md). Nonetheless, bir betik altyapısı en az bir `IPersist*` arabirimi (tercihen) tam olarak uygulamalıdır `IPersistStreamInit` , çünkü diğer ana bilgisayar uygulamaları bunları kullanmayı deneyebilir.  
  
 Aşağıdaki bölümlerde, bir Windows Scripting Engine 'in daha ayrıntılı bir şekilde uygulanması açıklanır.  
  
 Daha fazla bilgi için bkz. [Windows komut dosyası arabirimleri başvurusu](../winscript/reference/windows-script-interfaces-reference.md) .  
  
## <a name="registry-standard"></a>Kayıt defteri standardı  
 Windows komut dosyası altyapısı, kategori tanımlayıcılarını kullanarak kendisini tanımlayabilir. Windows betiği Şu anda iki kategori tanımlayıcısı tanımlıyor.  
  
|||  
|-|-|  
|Kategori|Description|  
|CATID_ActiveScript|Sınıf tanımlayıcılarının (CLSID), en düşük, [IActiveScript](../winscript/reference/iactivescript.md) arabirimi ve bir Kalıcılık mekanizması (, `IPersistStorage` `IPersistStreamInit` veya IPersistPropertyBag arabirimi) destekleyen Windows betik altyapıları olduğunu gösterir.|  
|CATID_ActiveScriptParse|CLSID 'lerin, en azından [IActiveScript](../winscript/reference/iactivescript.md) ve [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) arabirimlerini destekleyen Windows betik altyapıları olduğunu gösterir.|  
  
 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) , doğru bir Kalıcılık mekanizması olmasa da, işlev ile eşdeğer olan [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodunu destekler `IPersist*::InitNew` .  
  
## <a name="script-engine-states"></a>Betik altyapısı durumları  
 Belirli bir zamanda, bir Windows komut dosyası altyapısı birkaç durumdan birinde olabilir.  
  
|||  
|-|-|  
|Durum|Açıklama|  
|Başlatılmamış|Betik bir IPersist * arabirimi kullanılarak başlatılmamış veya yüklenmemiş ya da bir [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimi ayarlanmamış. Betik dosyası yüklenene kadar komut dosyası altyapısı bu durumdan genellikle kullanılamaz.|  
|başlatıldığını|Betik bir `IPersist*` arabirimle başlatılmış ve bir [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimi kümesine sahip, ancak ana bilgisayar nesnelerine bağlı değil ve olayları açmaya yönelik değil. Bu durumun,,, `IPersist*::Load` `IPersist*::InitNew` veya [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) yönteminin tamamlandığı ve [IActiveScript:: setscriptsite](../winscript/reference/iactivescript-setscriptsite.md) yönteminin çağrıldığı anlamına geldiğini unutmayın. Motor bu modda kod çalıştıramıyor. Motor, [IActiveScriptParse::P arseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) yöntemi aracılığıyla ana bilgisayarın kendisine geçirdiği kodu sıralar ve başlatılan duruma geçtikten sonra kodu yürütür.<br /><br /> Diller semantiklere göre değişebildiğinden, bu durum geçişini desteklemek için komut dosyası motorları gerekli değildir. Ancak, [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) metodunu destekleyen altyapıların bu durum geçişini desteklemesi gerekir. Konaklar bu geçişe hazırlanmalıdır ve uygun eylemi gerçekleştirebilir: geçerli komut dosyası altyapısını serbest bırakma, yeni bir betik altyapısı oluşturma ve, `IPersist*::Load` `IPersist*::InitNew` veya [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) (Ayrıca [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md)) çağrısı. Bu geçişin kullanılması yukarıdaki adımların en iyi duruma getirilmesi halinde düşünülmelidir. Betik altyapısının adlandırılmış öğelerin adları hakkında elde ettiği bilgilerin ve adlandırılmış öğeleri açıklayan tür bilgilerinin geçerli kalacağını unutmayın.<br /><br /> Diller yaygın farklılık gösterdiğinden, bu geçişin tam semantiğini tanımlamak zordur. En azından, komut dosyası motoru tüm olayların bağlantısını kesmelidir ve [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemini çağırarak elde edilen tüm SCRIPTINFO_IUNKNOWN işaretçilerini serbest bırakmalıdır. Komut dosyası yeniden çalıştırıldıktan sonra altyapının bu işaretçileri yeniden alması gerekir. Komut dosyası altyapısı Ayrıca betiği, dile uygun bir başlangıç durumuna geri sıfırlamalıdır. VBScript, örneğin, tüm değişkenleri sıfırlar ve SCRIPTTEXT_ISPERSISTENT bayrak kümesi ile [IActiveScriptParse::P arseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) çağırarak dinamik olarak eklenen herhangi bir kodu saklar. Diğer dillerin geçerli değerleri (kod/veri ayrımı olmadığından) veya iyi bilinen bir duruma sıfırlamasına (statik olarak başlatılan değişkenlere sahip diller de dahil olmak üzere) korumanız gerekebilir.<br /><br /> Başlatma durumuna geçişin aynı anlambilime sahip olması gerektiğini unutmayın (yani, komut dosyası altyapısını aynı durumda bırakmalıdır) `IPersist*::Save` , betik altyapısını kaydetmek ve sonra `IPersist*::Load` Yeni bir komut dosyası altyapısı yüklemek için çağırmak üzere, bu eylemler [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md)ile aynı semantiğe sahip olmalıdır. Daha önce desteklemeyen `IActiveScript::Clone` veya destek `IPersist*` `IActiveScript::Clone` `IPersist*` daha sonra eklendiyse bu tür bir geçişin yukarıdaki koşulları ihlal etmemesi için, başlatma durumuna geçişin nasıl davranması gerektiğini dikkatle belirten ya da dikkatli bir şekilde dikkate alması gereken betik altyapıları.<br /><br /> Bu başlangıç durumuna geçiş sırasında, komut dosyası altyapısı, uygun Yıkıcılardan sonra olay havuzları bağlantısını keser ve bu şekilde devam eder. Bu yok edicilerin yürütülmesinden kaçınmak için, ana bilgisayar önce, başlangıç durumuna geçmeden önce betiği bağlantısı kesik duruma taşıyabilir.<br /><br /> Çalışan bir betik iş parçacığını, geçerli olayları beklemeden iptal etmeden iptal etmek için [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) kullanın ve çalışmayı tamamlaması için.|  
|başlama|Başlatılmış durumdan başlangıç durumuna geçiş, altyapının başlatılmış durumda sıraya alınmış herhangi bir kodu yürütmesine neden olur. Motor, başlatılmış durumdayken kodu yürütebilir, ancak [IActiveScript:: Addnamedidıtem](../winscript/reference/iactivescript-addnameditem.md) yöntemiyle eklenen hiçbir olaya bağlı değildir. Motor, [IActiveScript:: GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) yönteminden elde edilen IDispatch arabirimini çağırarak veya [IActiveScriptParse::P arseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)öğesini çağırarak kodu yürütebilir. Daha fazla arka plan başlatma (Aşamalı yükleme) devam ediyor ve [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metodunu SCRIPTSTATE_CONNECTED bayrak kümesiyle çağırmak, başlatma tamamlanana kadar betiğin engellenmesine neden olabilir.|  
|bağlandı|Betiği, ana bilgisayar nesnelerinden gelen olayları açmak için yüklenir ve bağlanır. Bu, başlatılmış durumundan geçiş ise, komut dosyası altyapısı, bağlı durumu girmeden ve olaylara bağlanmadan önce, gerekli eylemleri gerçekleştirerek, başlatılan durumdan geçiş yapması gerekir.|  
|bağlantınızı|Betik yüklenir ve bir çalışma zamanı durumuna sahiptir, ancak ana bilgisayar nesnelerinden gelen olaylar için geçici olarak bağlantısı kesilir. Bu, mantıksal olarak (alınan olayları yoksayarak) veya fiziksel olarak (uygun bağlantı noktalarında ınewctionpoint:: Unadvise çağrılıyor) gerçekleştirilebilir. Bu, başlatılan durumdan geçişse, komut dosyası motoru, bağlantısı kesilmiş duruma girmeden önce, gerekli eylemleri gerçekleştirerek, başlatılan durumdan geçiş yapması gerekir. Devam eden olay havuzları durum değiştirilmeden önce tamamlanır (çalışan bir betik iş parçacığını iptal etmek için [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) kullanın). Bu durum, bu duruma geçiş betiğin sıfırlanmasına neden olmaz, betiğin çalışma zamanı durumu sıfırlanmaz ve bir komut dosyası başlatma yordamı yürütülmez.|  
|kapalı|Betik kapatıldı. Betik altyapısı artık çalışmaz ve çoğu Yöntem için hataları döndürür.|  
  
 Aşağıdaki çizimde çeşitli betik altyapısı durumları arasındaki ilişkiler gösterilmektedir ve bir durumdan diğerine geçiş yapılmasına neden olan Yöntemler gösterilmektedir.  
  
 Aşağıdaki çizimde, çeşitli durum geçişleri sırasında betik altyapısının gerçekleştirdiği eylemler gösterilmektedir.  
  
## <a name="scripting-engine-threading"></a>Scripting Engine Iş parçacığı  
 Bir Windows komut dosyası altyapısı birçok ortamda kullanılabileceği için, yürütme modelinin mümkün olduğunca esnek tutulması önemlidir. Örneğin, sunucu tabanlı bir konağın Windows betiğini verimli bir şekilde kullanırken çok iş parçacıklı tasarımı koruması gerekebilir. Aynı zamanda, yaygın bir uygulama gibi iş parçacığı kullanmayan bir konak, iş parçacığı yönetimiyle birlikte kullanılmamalıdır. Windows betiği, serbest iş parçacıklı bir betik altyapısının konağa geri çağrı yaptığı yolları kısıtlayarak bu dengeyi elde eder ve konakları bu yük 'ten boşaltır.  
  
 Sunucularda kullanılan betik altyapıları genellikle serbest iş parçacığı COM nesneleri olarak uygulanır. Bu, [IActiveScript](../winscript/reference/iactivescript.md) arabirimindeki yöntemlerin ve ilişkili arabirimlerinin, işlem içindeki herhangi bir iş parçacığından (sıralama olmadan) çağrılabilecek anlamına gelir. (Ne yazık ki, OLE Şu anda serbest iş parçacıklı nesnelerin işlem temelli sıralamasını desteklemediği için betik altyapısının işlem içi sunucu olarak uygulanması gerektiği anlamına gelir.) Eşitleme, betik altyapısının sorumluluğundadır. Dahili olarak yer olmayan ve çok iş parçacıklı olmayan dil modelleri için, eşitleme, bir mutex ile komut dosyası motoruna erişimi serileştirmek kadar basit olabilir. Kuşkusuz, [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)gibi bazı yöntemler bu şekilde serileştirilmemelidir, böylece takılmış bir betik başka bir iş parçacığından sonlandırılabilir.  
  
 [IActiveScript](../winscript/reference/iactivescript.md) genellikle ücretsiz iş parçacıklı olan olgu genellikle [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabiriminin ve ana bilgisayarın nesne modelinin de ücretsiz iş parçacıklı olması gerektiğini belirtir. Bu, özellikle de ana bilgisayarın kendi nesne modelinde tek iş parçacıklı veya apartman modeli ActiveX denetimleriyle tek iş parçacıklı bir Windows tabanlı uygulama olduğu yaygın durumda olduğundan, ana bilgisayar uygulamasının uygulanmasını oldukça zorlaştırır. Bu nedenle, aşağıdaki kısıtlamalar betik altyapısının [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)kullanımına yerleştirilir:  
  
 Betik sitesi her zaman bir konak iş parçacığı bağlamında çağırılır. Diğer bir deyişle, komut dosyası altyapısı hiçbir şekilde komut dosyası altyapısının oluşturduğu bir iş parçacığının bağlamında, ancak [IActiveScript](../winscript/reference/iactivescript.md) ve türevlerinin üzerinden çağrılan bir komut dosyası motoru yöntemi içinden, bir Windows iletisi aracılığıyla veya konağın nesne modelindeki bir olay kaynağından çağrılır.  
  
 Betik sitesi bir basit iş parçacığı durum denetimi yöntemi (örneğin, [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) yöntemi) veya [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md) yönteminden hiçbir şekilde çağrılmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Windows Komut Dosyası Arabirimleri](../winscript/windows-script-interfaces.md)
