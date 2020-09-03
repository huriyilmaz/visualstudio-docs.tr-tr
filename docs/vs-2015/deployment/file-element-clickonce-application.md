---
title: '&lt;Dosya &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88fce548d5adbd6d4dc930db767fd3e52690490b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148772"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;Dosya &gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İndirilen ve uygulama tarafından kullanılan tüm derleme olmayan dosyaları tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `file`Öğesi isteğe bağlıdır. Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gereklidir. Dosyanın adını tanımlar.|  
|`size`|Gereklidir. Dosyanın boyutunu bayt cinsinden belirtir.|  
|`group`|`optional`Öznitelik belirtilmemişse veya olarak ayarlandıysa isteğe bağlı `false` ; ise gereklidir `optional` `true` . Bu dosyanın ait olduğu grubun adı. Ad, geliştirici tarafından seçilen herhangi bir Unicode dize değeri olabilir ve sınıfı ile isteğe bağlı dosyaları indirmek için kullanılır <xref:System.Deployment.Application.ApplicationDeployment> .|  
|`optional`|İsteğe bağlı. Uygulama ilk çalıştırıldığında bu dosyanın indirilmesinin gerekip gerekmediğini veya uygulamanın istek üzerine istemesi için dosyanın yalnızca sunucuda bulunup bulunmaması gerektiğini belirtir. `false`Veya tanımlanmamışsa, uygulama ilk kez çalıştırıldığında veya yüklendiğinde dosya indirilir. `true` `group` Uygulama bildiriminin geçerli olması için bir belirtilmesi gerekir. `optional``writeableType`değeri ile belirtilirse true olamaz `applicationData` .|  
|`writeableType`|İsteğe bağlı. Bu dosyanın bir veri dosyası olduğunu belirtir. Şu anda tek geçerli değer `applicationData` .|  
  
## <a name="typelib"></a>TypeLib  
 `typelib`Öğesi, dosya öğesinin isteğe bağlı bir alt öğesidir. Öğesi, COM bileşenine ait olan tür kitaplığını tanımlar. Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`tlbid`|Gereklidir. Tür kitaplığına atanan GUID.|  
|`version`|Gereklidir. Tür kitaplığının sürüm numarası.|  
|`helpdir`|Gereklidir. Bileşen için yardım dosyalarını içeren dizin. Sıfır uzunlukta olabilir.|  
|`resourceid`|İsteğe bağlı. Yerel ayar tanımlayıcısının (LCıD) onaltılık dize temsili. 0x ön eki olmadan ve önünde sıfır olmadan, en çok dört onaltılık basamak olur. LCıD bağımsız bir alt dil tanımlayıcısına sahip olabilir.|  
|`flags`|İsteğe bağlı. Bu tür kitaplığı için tür kitaplığı bayraklarının dize temsili. Özellikle, "RESTRICTED", "CONTROL", "HIDDEN" ve "HASDISKıMAGE" gibi bir tane olmalıdır.|  
  
## <a name="comclass"></a>comClass  
 Öğesi, `comClass` öğesinin isteğe bağlı bir alt öğesidir `file` , ancak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama kayıtsız com kullanarak DAĞıTMAYı amaçlayan bir com bileşeni içeriyorsa gereklidir. Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clsid`|Gereklidir. GUID olarak ifade edilen COM bileşeninin sınıf KIMLIĞI.|  
|`description`|İsteğe bağlı. Sınıf adı.|  
|`threadingModel`|İsteğe bağlı. İşlem içi COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılmaz. Bileşen, istemcinin ana iş parçacığında oluşturulur ve diğer iş parçacıklarından çağrılar bu iş parçacığına hazırlanır. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `Apartment`, `Free` , `Both` , ve `Neutral` .|  
|`tlbid`|İsteğe bağlı. Bu COM bileşenine ait tür kitaplığı için GUID.|  
|`progid`|İsteğe bağlı. COM bileşeniyle ilişkili sürüme bağımlı programlama tanımlayıcısı. Öğesinin biçimi `ProgID` `<vendor>.<component>.<version>` .|  
|`miscStatus`|İsteğe bağlı. Bütünleştirilmiş kod bildiriminde yinelenen öğeler `MiscStatus` kayıt defteri anahtarı tarafından belirtilen bilgileri. `miscStatusIcon`,, `miscStatusContent` `miscStatusDocprint` , Veya `miscStatusThumbnail` özniteliklerinin değerleri bulunamazsa, içinde listelenen karşılık gelen varsayılan değer `miscStatus` eksik öznitelikler için kullanılır. Değer, aşağıdaki tablodaki öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı, `MiscStatus` kayıt defteri anahtarı değerleri gerektiren BIR ocx sınıfınise bu özniteliği kullanabilirsiniz.|  
|`miscStatusIcon`|İsteğe bağlı. Bütünleştirilmiş kod bildiriminde yinelenen DVASPECT_ICON tarafından belirtilen bilgiler. Bir nesnenin simgesini sağlayabilir. Değer, aşağıdaki tablodaki öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı, `Miscstatus` kayıt defteri anahtarı değerleri gerektiren BIR ocx sınıfınise bu özniteliği kullanabilirsiniz.|  
|`miscStatusContent`|İsteğe bağlı. Bütünleştirilmiş kod bildiriminde yinelenen DVASPECT_CONTENT tarafından belirtilen bilgiler. Bu, bir ekran veya yazıcı için görüntülenebilen bir bileşik belge sağlayabilir. Değer, aşağıdaki tablodaki öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı, `MiscStatus` kayıt defteri anahtarı değerleri gerektiren BIR ocx sınıfınise bu özniteliği kullanabilirsiniz.|  
|`miscStatusDocPrint`|İsteğe bağlı. Bütünleştirilmiş kod bildiriminde yinelenen DVASPECT_DOCPRINT tarafından belirtilen bilgiler. Bir yazıcıya yazdırılmış gibi ekranda görüntülenebilen bir nesne temsili sağlayabilir. Değer, aşağıdaki tablodaki öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı, `MiscStatus` kayıt defteri anahtarı değerleri gerektiren BIR ocx sınıfınise bu özniteliği kullanabilirsiniz.|  
|`miscStatusThumbnail`|İsteğe bağlı. Bütünleştirilmiş kod bildiriminde yinelenen DVASPECT_THUMBNAIL tarafından belirtilen bilgiler. Göz atma aracında görüntülenebilen bir nesnenin küçük resmini sağlayabilir. Değer, aşağıdaki tablodaki öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı, `MiscStatus` kayıt defteri anahtarı değerleri gerektiren BIR ocx sınıfınise bu özniteliği kullanabilirsiniz.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Öğesi, `comInterfaceExternalProxyStub` öğesinin isteğe bağlı bir alt öğesidir `file` , ancak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama kayıtsız com kullanarak dağıtmayı amaçladığı bir com bileşeni içeriyorsa, gerekli olabilir. Öğesi aşağıdaki öznitelikleri içerir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`iid`|Gereklidir. Bu proxy tarafından sunulan arabirim KIMLIĞI (IID). IID 'nin çevreleyen ayraçları olmalıdır.|  
|`baseInterface`|İsteğe bağlı. Tarafından başvurulan arabirimin türetildiği arabirimin IID `iid` 'si.|  
|`numMethods`|İsteğe bağlı. Arabirim tarafından uygulanan yöntemlerin sayısı.|  
|`name`|İsteğe bağlı. Arabirimin, kodda görüneceği şekilde adı.|  
|`tlbid`|İsteğe bağlı. Özniteliği tarafından belirtilen arabirimin açıklamasını içeren tür kitaplığı `iid` .|  
|`proxyStubClass32`|İsteğe bağlı. Bir IID 'yi 32 bitlik ara dll 'lerde bir CLSID ile eşleştirir.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Öğesi, `comInterfaceProxyStub` öğesinin isteğe bağlı bir alt öğesidir `file` , ancak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama kayıtsız com kullanarak dağıtmayı amaçladığı bir com bileşeni içeriyorsa, gerekli olabilir. Öğesi aşağıdaki öznitelikleri içerir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`iid`|Gereklidir. Bu proxy tarafından sunulan arabirim KIMLIĞI (IID). IID 'nin çevreleyen ayraçları olmalıdır.|  
|`baseInterface`|İsteğe bağlı. Tarafından başvurulan arabirimin türetildiği arabirimin IID `iid` 'si.|  
|`numMethods`|İsteğe bağlı. Arabirim tarafından uygulanan yöntemlerin sayısı.|  
|`Name`|İsteğe bağlı. Arabirimin, kodda görüneceği şekilde adı.|  
|`Tlbid`|İsteğe bağlı. Özniteliği tarafından belirtilen arabirimin açıklamasını içeren tür kitaplığı `iid` .|  
|`proxyStubClass32`|İsteğe bağlı. Bir IID 'yi 32 bitlik ara dll 'lerde bir CLSID ile eşleştirir.|  
|`threadingModel`|İsteğe bağlı. İsteğe bağlı. İşlem içi COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılmaz. Bileşen, istemcinin ana iş parçacığında oluşturulur ve diğer iş parçacıklarından çağrılar bu iş parçacığına hazırlanır. Aşağıdaki listede geçerli değerler gösterilmektedir:<br /><br /> `Apartment`, `Free` , `Both` , ve `Neutral` .|  
  
## <a name="windowclass"></a>windowClass  
 Öğesi, `windowClass` öğesinin isteğe bağlı bir alt öğesidir `file` , ancak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama kayıtsız com kullanarak dağıtmayı amaçladığı bir com bileşeni içeriyorsa, gerekli olabilir. Öğesi, bir sürümü uygulanmış olması gereken COM bileşeni tarafından tanımlanan bir pencere sınıfına başvurur. Öğesi aşağıdaki öznitelikleri içerir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`versioned`|İsteğe bağlı. Kayıt sırasında kullanılan iç pencere sınıfı adının, pencere sınıfını içeren derlemenin sürümünü içerip içermediğini denetler. Bu özniteliğin değeri `yes` veya olabilir `no` . Varsayılan değer: `yes`. Değer `no` yalnızca, aynı pencere sınıfı yan yana bir bileşen ve yan yana olmayan bir bileşen tarafından tanımlanmışsa ve bunları aynı pencere sınıfı olarak değerlendirmek istiyorsanız kullanılmalıdır. Pencere sınıfı kaydına ilişkin olağan kuralların, yalnızca pencere sınıfını kaydeden ilk bileşen kendisine uygulanan bir sürüme sahip olmadığı için bu uygulamayı kaydedebileceğini unutmayın.|  
  
## <a name="hash"></a>hash  
 `hash`Öğesi, öğesinin isteğe bağlı bir alt öğesidir `file` . `hash`Öğesinde hiç öznitelik yok.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] herhangi bir dosyanın dağıtımdan sonra değişmediğinden emin olmak için, bir uygulamadaki tüm dosyaların bir güvenlik denetimi olarak algoritmik karmasını kullanır. `hash`Öğe dahil değilse, bu denetim gerçekleştirilmez. Bu nedenle, `hash` öğesinin atlanması önerilmez.  
  
 Bir bildirim, karma olmayan bir dosya içeriyorsa, kullanıcılar karma olmayan bir dosyanın içeriğini doğrulayamadığından, bu bildirim dijital olarak imzalanamıyor.  
  
## <a name="dsigtransforms"></a>dsig: dönüşümler  
 `dsig:Transforms`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:Transforms`Öğesinde hiç öznitelik yok.  
  
## <a name="dsigtransform"></a>dsig: dönüştürme  
 `dsig:Transform`Öğesi, öğesinin gerekli bir alt öğesidir `dsig:Transforms` . `dsig:Transform`Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig: DigestMethod  
 `dsig:DigestMethod`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:DigestMethod`Öğesi aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özeti hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 `dsig:DigestValue`Öğesi, öğesinin gerekli bir alt öğesidir `hash` . `dsig:DigestValue`Öğesinde hiç öznitelik yok. Metin değeri, belirtilen dosya için hesaplanan karmadır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, uygulamayı oluşturan tüm derleme olmayan dosyaları ve özellikle de dosya doğrulaması için karma değerleri tanımlar. Bu öğe ayrıca dosyayla ilişkili bileşen nesne modeli (COM) yalıtım verilerini de içerebilir. Bir dosya değişirse, uygulama bildirim dosyasının değişikliği yansıtması için de güncelleştirilmeleri gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `file` kullanılarak dağıtılan bir uygulama için bir uygulama bildirimindeki öğeleri gösterir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
