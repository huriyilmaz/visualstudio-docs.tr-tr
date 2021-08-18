---
title: '&lt;file &gt; Öğesi (ClickOnce Application) | Microsoft Docs'
description: dosya öğesi, uygulama tarafından indirilen ve kullanılan tüm bütünleşik olmayan dosyaları tanımlar. Dosya öğesi isteğe bağlıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 68733629b26b4640e63919aaa4f9d07d0c70f972
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051605"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file &gt; öğesi (ClickOnce uygulama)
Uygulama tarafından indirilen ve kullanılan tüm bütünleşik olmayan dosyaları tanımlar.

## <a name="syntax"></a>Syntax

```xml
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
 öğesi `file` isteğe bağlıdır. öğesi aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Dosyanın adını tanımlar.|
|`size`|Gereklidir. Dosyanın boyutunu bayt cinsinden belirtir.|
|`group`|özniteliği `optional` belirtilmezse veya olarak ayarlanmazsa `false` isteğe bağlı; ise `optional` `true` gereklidir. Bu dosyanın ait olduğu grubun adı. Ad, geliştirici tarafından seçilen herhangi bir Unicode dize değeri olabilir ve sınıfıyla isteğe bağlı dosyaları indirmek için <xref:System.Deployment.Application.ApplicationDeployment> kullanılır.|
|`optional`|İsteğe bağlı. Bu dosyanın uygulama ilk kez çalıştırılana kadar indir mi, yoksa uygulama isteğe bağlı olarak istenene kadar dosyanın yalnızca sunucuda mı yer alası gerektiğini belirtir. Tanımlanmamış `false` veya tanımlanmamışsa, uygulama ilk kez çalıştırıldı veya yüklendikten sonra dosya indirilir. `true`ise, `group` uygulama bildiriminin geçerli olması için bir belirtilmelidir. `optional` değeriyle `writeableType` belirtilirse true `applicationData` olamaz.|
|`writeableType`|İsteğe bağlı. Bu dosyanın bir veri dosyası olduğunu belirtir. Şu anda tek geçerli değer `applicationData` değeridir.|

## <a name="typelib"></a>Typelib
 öğesi, `typelib` dosya öğesinin isteğe bağlı bir alt öğesidir. öğesi COM bileşenine ait tür kitaplığını açıklar. öğesi aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`tlbid`|Gereklidir. Tür kitaplığına atanan GUID.|
|`version`|Gereklidir. Tür kitaplığının sürüm numarası.|
|`helpdir`|Gereklidir. Bileşenin Yardım dosyalarını içeren dizin. Sıfır uzunluklu olabilir.|
|`resourceid`|İsteğe bağlı. Yerel tanımlayıcının (LCID) onaltılık dize gösterimi. 0x ön eki olmadan ve önüne sıfırlar olmadan bir veya dört onaltılık basamaktan oluşur. LCID,nötr bir alt dil tanımlayıcısına sahip olabilir.|
|`flags`|İsteğe bağlı. Bu tür kitaplığı için tür kitaplığı bayraklarının dize gösterimi. Özel olarak, "RESTRICTED", "CONTROL", "HIDDEN" ve "HASDISKIMAGE" dosyalarından biri olması gerekir.|

## <a name="comclass"></a>comClass
 öğesi, öğesinin isteğe bağlı bir alt öğesidir, ancak uygulama kayıtsız COM kullanarak dağıtmayı niyetli bir `comClass` `file` COM bileşeni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içeriyorsa gereklidir. öğesi aşağıdaki özniteliklere sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`clsid`|Gereklidir. COM bileşeninin GUID olarak ifade eden sınıf kimliği.|
|`description`|İsteğe bağlı. Sınıf adı.|
|`threadingModel`|İsteğe bağlı. İşlem içinde COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılmaz. Bileşeni istemcinin ana iş parçacığında oluşturulur ve diğer iş parçacıklarından gelen çağrılar bu iş parçacığına sıralandı. Aşağıdaki listede geçerli değerler görüntülenir:<br /><br /> `Apartment`, `Free` `Both` , ve `Neutral` .|
|`tlbid`|İsteğe bağlı. Bu COM bileşeninin tür kitaplığı için GUID.|
|`progid`|İsteğe bağlı. COM bileşeniyle ilişkili sürüme bağımlı programlı tanımlayıcı. `ProgID` `<vendor>.<component>.<version>` biçimidir.|
|`miscStatus`|İsteğe bağlı. Derleme bildiriminde kayıt defteri anahtarı tarafından sağlanan bilgileri `MiscStatus` yineler. , , `miscStatusIcon` veya öznitelikleri `miscStatusContent` için değerler `miscStatusDocprint` `miscStatusThumbnail` bulunamasa, eksik öznitelikler için içinde `miscStatus` listelenen karşılık gelen varsayılan değer kullanılır. Değer, aşağıdaki tabloda yer alan öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı kayıt defteri anahtar değerleri gerektiren bir OCX sınıfı ise bu `MiscStatus` özniteliği kullanabilirsiniz.|
|`miscStatusIcon`|İsteğe bağlı. Derleme bildiriminde, uygulama tarafından sağlanan bilgileri DVASPECT_ICON. Bir nesnenin simgesini sağlar. Değer, aşağıdaki tabloda yer alan öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı kayıt defteri anahtar değerleri gerektiren bir OCX sınıfı ise bu `Miscstatus` özniteliği kullanabilirsiniz.|
|`miscStatusContent`|İsteğe bağlı. Derleme bildiriminde, DVASPECT_CONTENT tarafından sağlanan bilgileri DVASPECT_CONTENT. Bir ekran veya yazıcı için değiştirilebilir bileşik bir belge sağlar. Değer, aşağıdaki tabloda yer alan öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı kayıt defteri anahtar değerleri gerektiren bir OCX sınıfı ise bu `MiscStatus` özniteliği kullanabilirsiniz.|
|`miscStatusDocPrint`|İsteğe bağlı. Derleme bildiriminde, DVASPECT_DOCPRINT tarafından sağlanan bilgileri DVASPECT_DOCPRINT. Bir yazıcıya yazdırılmış gibi ekranda görüntülenebilir bir nesne gösterimi sağlar. Değer, aşağıdaki tabloda yer alan öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı kayıt defteri anahtar değerleri gerektiren bir OCX sınıfı ise bu `MiscStatus` özniteliği kullanabilirsiniz.|
|`miscStatusThumbnail`|İsteğe bağlı. Bir derleme bildiriminde, uygulama tarafından sağlanan bilgileri DVASPECT_THUMBNAIL. Bir gözatma aracında görüntülenebilir bir nesnenin küçük resmini sağlar. Değer, aşağıdaki tabloda yer alan öznitelik değerlerinin virgülle ayrılmış bir listesi olabilir. COM sınıfı kayıt defteri anahtar değerleri gerektiren bir OCX sınıfı ise bu `MiscStatus` özniteliği kullanabilirsiniz.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 öğesi, öğesinin isteğe bağlı bir alt öğesidir, ancak uygulama kayıtsız COM kullanarak dağıtmayı niyetli bir COM bileşeni `comInterfaceExternalProxyStub` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içeriyorsa gerekli olabilir. öğesi aşağıdaki öznitelikleri içerir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`iid`|Gereklidir. Bu ara sunucu tarafından sunulan arabirim kimliği (IID). IID'nin çevresinde ayraçlar olması gerekir.|
|`baseInterface`|İsteğe bağlı. Başvurulan arabirimin türetilen arabiriminin `iid` IID'i.|
|`numMethods`|İsteğe bağlı. Arabirim tarafından uygulanan yöntemlerin sayısı.|
|`name`|İsteğe bağlı. Arabirimin kodda görünecek adı.|
|`tlbid`|İsteğe bağlı. özniteliği tarafından belirtilen arabirimin açıklamasını içeren tür `iid` kitaplığı.|
|`proxyStubClass32`|İsteğe bağlı. Haritalar 32 bit proxy DLL'leri içinde clSID'ye bir IID sağlar.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 öğesi, öğesinin isteğe bağlı bir alt öğesidir, ancak uygulama kayıtsız COM kullanarak dağıtmayı niyetli bir COM bileşeni `comInterfaceProxyStub` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içeriyorsa gerekli olabilir. öğesi aşağıdaki öznitelikleri içerir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`iid`|Gereklidir. Bu ara sunucu tarafından sunulan arabirim kimliği (IID). IID'nin çevresinde ayraçlar olması gerekir.|
|`baseInterface`|İsteğe bağlı. Başvurulan arabirimin türetilen arabiriminin `iid` IID'i.|
|`numMethods`|İsteğe bağlı. Arabirim tarafından uygulanan yöntemlerin sayısı.|
|`Name`|İsteğe bağlı. Arabirimin kodda görünecek adı.|
|`Tlbid`|İsteğe bağlı. özniteliği tarafından belirtilen arabirimin açıklamasını içeren tür `iid` kitaplığı.|
|`proxyStubClass32`|İsteğe bağlı. Haritalar 32 bit proxy DLL'leri içinde clSID'ye bir IID sağlar.|
|`threadingModel`|İsteğe bağlı. İsteğe bağlı. İşlem içinde COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılmaz. Bileşeni istemcinin ana iş parçacığında oluşturulur ve diğer iş parçacıklarından gelen çağrılar bu iş parçacığına sıralandı. Aşağıdaki listede geçerli değerler görüntülenir:<br /><br /> `Apartment`, `Free` `Both` , ve `Neutral` .|

## <a name="windowclass"></a>Windowclass
 öğesi, öğesinin isteğe bağlı bir alt öğesidir, ancak uygulama kayıtsız COM kullanarak dağıtmayı niyetli bir COM bileşeni `windowClass` `file` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içeriyorsa gerekli olabilir. öğesi, COM bileşeni tarafından tanımlanan ve bir sürümün uygulanmış olması gereken bir pencere sınıfına başvurur. öğesi aşağıdaki öznitelikleri içerir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`versioned`|İsteğe bağlı. Kayıtta kullanılan iç pencere sınıfı adının, pencere sınıfını içeren derlemenin sürümünü içerip içerip içerip içerdiğini kontrol eder. Bu özniteliğin değeri veya `yes` `no` olabilir. Varsayılan değer: `yes`. Değer yalnızca aynı pencere sınıfı bir yan yana bileşen ve eşdeğer bir yan yana bileşen tarafından tanımlanmışsa ve bunları aynı pencere sınıfı olarak kabul etmek `no` istediğinizde kullanılmalıdır. Pencere sınıfı kaydıyla ilgili her zamanki kuralların geçerli olduğunu unutmayın; yalnızca pencere sınıfını kaydeden ilk bileşen, ona uygulanmış bir sürümüne sahip değildir.|

## <a name="hash"></a>hash
 öğesi, `hash` öğesinin isteğe bağlı bir alt `file` öğesidir. öğesinin `hash` özniteliği yoktur.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , dağıtımdan sonra dosyalardan hiçbirinin değişmediğini sağlamak için güvenlik denetimi olarak bir uygulamanın tüm dosyalarının algoritma karması kullanır. Öğe `hash` dahil yoksa, bu denetim gerçekleştirlanmaz. Bu nedenle, `hash` öğesinin yok kullanılması önerilmez.

 Bir bildirim karmalanmamış bir dosya içeriyorsa, kullanıcılarhazırlanmamış bir dosyanın içeriğini doğrulayamay olduğundan bu bildirim dijital olarak imzalanamaz.

## <a name="dsigtransforms"></a>dsig:Transforms
 `dsig:Transforms`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesinin `dsig:Transforms` özniteliği yoktur.

## <a name="dsigtransform"></a>dsig:Transform
 `dsig:Transform`öğesi, öğesinin gerekli bir alt `dsig:Transforms` öğesidir. öğesi `dsig:Transform` aşağıdaki özniteliklere sahip.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosyanın özetini hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` değeridir. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 `dsig:DigestMethod`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesi `dsig:DigestMethod` aşağıdaki özniteliklere sahip.

| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosyanın özetini hesaplamak için kullanılan algoritma. Şu anda tarafından kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` değeridir. |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 `dsig:DigestValue`öğesi, öğesinin gerekli bir alt `hash` öğesidir. öğesinin `dsig:DigestValue` özniteliği yoktur. Metin değeri, belirtilen dosya için hesaplanan karmadır.

## <a name="remarks"></a>Açıklamalar
 Bu öğe, uygulamayı ve özellikle de dosya doğrulama karma değerlerini tüm bir bütün olarak olmayan dosyaları tanımlar. Bu öğe, dosyayla ilişkili Bileşen Nesne Modeli (COM) yalıtım verilerini de içerebilir. Bir dosya değişirse, uygulama bildirim dosyasının da değişikliği yansıtacak şekilde güncelleştirilmiş olması gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, kullanılarak `file` dağıtılan bir uygulamanın uygulama bildiriminde yer alan öğeleri [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gösterir.

```xml
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

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)