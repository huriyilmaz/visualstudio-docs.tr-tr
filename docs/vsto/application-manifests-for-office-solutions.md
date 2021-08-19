---
title: Office çözümleri için uygulama bildirimleri
description: uygulama bildiriminin bir Microsoft Office çözümüne yüklenen derlemeleri açıklayan bir XML dosyası olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2e7150adfe0c3480de65acbdaa0e26f4b33effb4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038285"
---
# <a name="application-manifests-for-office-solutions"></a>Office çözümleri için uygulama bildirimleri
  uygulama bildirimi, Microsoft Office çözümüne yüklenen derlemeleri açıklayan bir XML dosyasıdır. Visual Studio Microsoft Office geliştirme araçları [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md) başvurusunda tanımlanan uygulama bildirimi şemasını kullanır.

 Office çözümleri için uygulama bildirimleri aşağıdaki [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] öğeleri ve öznitelikleri kullanır.

|Öğe|Açıklama|Öznitelikler|
|-------------|-----------------|----------------|
|[&#60;derleme&#62; öğesi &#40;ClickOnce uygulama&#41;](../deployment/assembly-element-clickonce-deployment.md)|Gereklidir. Üst düzey öğe.|**manifestVersion**|
|[&#60;assemblyıdentity&#62; öğe &#40;ClickOnce uygulama&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Gereklidir. [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Uygulamanın birincil derlemesini tanımlar.|**ada**<br /><br /> **Sürüm**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **dildir**|
|[&#60;trustınfo&#62; öğe &#40;ClickOnce uygulama&#41;](../deployment/trustinfo-element-clickonce-application.md)|Uygulama güvenlik gereksinimlerini tanımlar.|Hiçbiri|
|[&#60;giriş noktası&#62; öğe &#40;ClickOnce uygulama&#41;](../deployment/entrypoint-element-clickonce-application.md)|Gereklidir. Yürütme için uygulama kodu giriş noktasını tanımlar.|**ada**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;bağımlılık&#62; öğe &#40;ClickOnce uygulama&#41;](../deployment/dependency-element-clickonce-deployment.md)|Gereklidir. Uygulamanın çalışması için gereken her bağımlılığı tanımlar. İsteğe bağlı olarak, önceden yüklenmesi gereken derlemeleri tanımlar.|Hiçbiri|
|[&#60;dosya&#62; öğe &#40;ClickOnce uygulama&#41;](../deployment/file-element-clickonce-application.md)|Gereklidir. Uygulama tarafından kullanılan derleme olmayan her dosyayı tanımlar. , Dosyayla ilişkili bileşen nesne modeli (COM) yalıtım verilerini içerebilir.|**ada**<br /><br /> **boyutla**|

 Office çözümleri için uygulama bildirimlerinin ad alanında aşağıdaki öğesi vardır `co.v1` .

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Bu uygulama bildirimleri de ad alanında aşağıdaki öğelere ve özniteliklere sahiptir `vstav3` .

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Öğe|Açıklama|Öznitelikler|
|-------------|-----------------|----------------|
|[&#60;customhostbelirtilen&#62; öğesi &#40;Office geliştirme Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Gereklidir. bildirimi özel olarak bir Office çözümü olarak işaretler.|Hiçbiri|
|[&#60;addın&#62; öğesi &#40;Office geliştirme Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Gereklidir. Giriş noktalarını tek bir ad alanına depolar.|Hiçbiri|
|[&#60;entryPointsCollection&#62; öğesi &#40;Office geliştirme Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Gereklidir. bir veya daha fazla Office çözümü için tüm derlemeleri gruplandırır.|**id**|
|[&#60;&#62; öğe &#40;Office geliştirme Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Gereklidir. tüm derlemeleri bir Office çözümü çalıştıracak şekilde gruplandırır.|Hiçbiri|
|[&#60;giriş noktası&#62; öğe &#40;Office geliştirme Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Gereklidir. Office çözümünde çalıştırılacak derlemeyi tanımlar.|**sınıfı**<br /><br /> **Sözleşmesi**|
|[Visual Studio&#62;&#60;güncelleştirme &#40;Office geliştirme&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Gereklidir. Çözüm için güncelleştirmeleri yapılandırır.|**etkinletir**<br /><br /> **dolmadan**|
|[&#60;&#62; öğe &#40;Visual Studio Office geliştirme&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|İsteğe bağlı. Office çözümleri yüklendikten sonra çalıştırılan tüm dağıtım sonrası eylemlerini gruplandırır.|Hiçbiri|
|[Visual Studio&#62;&#60;postaeylemi &#40;Office geliştirme&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|İsteğe bağlı. Dağıtım sonrası eylemi tanımlar.|Hiçbiri|
|[&#60;postactiondata&#62; öğesi &#40;Office geliştirme Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|İsteğe bağlı. Dağıtım sonrası eylemi için verileri yapılandırır.|Hiçbiri|
|[&#60;uygulama&#62; öğesi &#40;Office geliştirme Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Gereklidir. Uygulamaya özgü bilgileri tek bir düğüme kaydırır.|Hiçbiri|
|[&#60;özelleştirmeler&#62; öğe &#40;Office geliştirme Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Gereklidir. Uygulamaya özgü tüm bilgileri ayrı bir ad alanında depolar.|Hiçbiri|
|[&#60;özelleştirme&#62; öğe &#40;Office geliştirme Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Gereklidir. Uygulama konağına özgü bilgileri ayrı bir ad alanında depolar.|**özniteliði**|
|[&#60;belge&#62; öğe &#40;Office geliştirme Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Yalnızca belge düzeyi çözümler için gereklidir. Özelleştirmeden özel bilgileri depolar.|**SolutionID**|
|[&#60;appAddin&#62; Öğesi &#40;Office Geliştirme Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Yalnızca uygulama düzeyindeki çözümler için gereklidir. Özelleştirmeye özgü bilgileri depolar.|**uygulama**<br /><br /> **Loadbehavior**<br /><br /> **Keyname**|
|[&#60;friendlyName&#62; Öğesi &#40;Office Geliştirme Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|İsteğe bağlı. VSTO Eklentileri'nin yüklü listesinde görünen VSTO depolar.|Hiçbiri|
|[&#60;Geliştirme&#62; Öğesi &#40;Office açıklaması Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Yalnızca eklenti VSTO gereklidir. Yüklü programlar listesinde görüntülenen açıklamayı depolar.|Hiçbiri|
|[&#60;formRegions&#62; Öğesi &#40;Office Geliştirme Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Yalnızca form Outlook VSTO ek eklentiler için gereklidir.|Hiçbiri|
|[&#60;formRegion&#62; Öğesi &#40;Office Geliştirme Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Yalnızca form Outlook VSTO ek eklentiler için gereklidir.|**Ad**|
|[&#60;vstoRuntime&#62; Öğesi &#40;Office Geliştirme Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Gereklidir. Office çözümü tarafından desteklenen Office için Visual Studio Araçları çalışma zamanının belirli bir Office açıklar.|**Sürüm**<br /><br /> **Sürüm**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Açıklamalar
 Uygulama ve dağıtım bildirimlerini uygulama ve dağıtım bildirimlerini Office düzenleyebilirsiniz. Daha sonra, uygulama ve dağıtım bildirimlerini yeniden imzalamak için Bildirim Oluşturma ve Düzenleme Aracı *(* mage.exeve *mageui.exe).* Daha fazla bilgi için, [bkz. How to: Re-sign application and deployment manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Dosya konumu
 Uygulama bildirimi, çözümün tek bir sürümüne özgüdür. Bu nedenle uygulama bildirimlerinin dağıtım bildirimlerinden ayrı olarak depolanmış olması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]sürüme özgü dosyaları, yayımlama klasöründeki Uygulama Dosyaları alt  dizininde ilişkili sürümden sonra adlı bir alt dizine yer alan bir alt dizine yer sağlar.

## <a name="file-name-syntax"></a>Dosya adı söz dizimi
 Bir uygulama bildirim dosyasının **adı, assemblyIdentity** öğesinde tanımlanan uygulamanın tam adı ve uzantısı ve *ardından .manifest uzantısına sahip olması gerekir.* Örneğin, uygulama özelleştirmesini ifade eden bir *OutlookAddIn1.dll* dosya adı söz dizimi kullanılır.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)