---
title: Office çözümleri için uygulama bildirimleri
description: Uygulama bildiriminin bir Microsoft Office çözümüne yüklenen derlemeleri açıklayan bir XML dosyası olduğunu öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a16d0f438d06cbfa48538bb3e370ed9b334ad16
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847929"
---
# <a name="application-manifests-for-office-solutions"></a>Office çözümleri için uygulama bildirimleri
  Uygulama bildirimi, Microsoft Office çözümüne yüklenen derlemeleri açıklayan bir XML dosyasıdır. Visual Studio 'daki Microsoft Office geliştirme araçları, [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md) başvurusunda tanımlanan uygulama bildirimi şemasını kullanır.

 Office çözümleri için uygulama bildirimleri aşağıdaki [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] öğeleri ve öznitelikleri kullanır.

|Öğe|Açıklama|Öznitelikler|
|-------------|-----------------|----------------|
|[&#60;derleme&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/assembly-element-clickonce-deployment.md)|Gereklidir. Üst düzey öğe.|**manifestVersion**|
|[&#60;assemblyIdentity&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Gereklidir. [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Uygulamanın birincil derlemesini tanımlar.|**ada**<br /><br /> **Sürüm**<br /><br /> **publicKeyToken**<br /><br /> **processorArchitecture**<br /><br /> **dildir**|
|[&#60;TrustInfo&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/trustinfo-element-clickonce-application.md)|Uygulama güvenlik gereksinimlerini tanımlar.|Hiçbiri|
|[&#60;giriş noktası&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/entrypoint-element-clickonce-application.md)|Gereklidir. Yürütme için uygulama kodu giriş noktasını tanımlar.|**ada**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;bağımlılık&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/dependency-element-clickonce-deployment.md)|Gereklidir. Uygulamanın çalışması için gereken her bağımlılığı tanımlar. İsteğe bağlı olarak, önceden yüklenmesi gereken derlemeleri tanımlar.|Hiçbiri|
|[&#60;dosya&#62; öğesi ClickOnce uygulaması &#40;&#41;](../deployment/file-element-clickonce-application.md)|Gereklidir. Uygulama tarafından kullanılan derleme olmayan her dosyayı tanımlar. , Dosyayla ilişkili bileşen nesne modeli (COM) yalıtım verilerini içerebilir.|**ada**<br /><br /> **boyutla**|

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
|[&#60;Customhostbelirtilen&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Gereklidir. Bildirimi özel olarak bir Office çözümü olarak işaretler.|Hiçbiri|
|[&#60;AddIn&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Gereklidir. Giriş noktalarını tek bir ad alanına depolar.|Hiçbiri|
|[&#60;entryPointsCollection&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Gereklidir. Bir veya daha fazla Office çözümü için tüm derlemeleri gruplandırır.|**id**|
|[&#60;entryPoints&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Gereklidir. Tüm derlemeleri bir Office çözümünü çalıştıracak şekilde gruplandırır.|Hiçbiri|
|[&#60;entryPoint&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Gereklidir. Bir Office çözümünde çalıştırılacak derlemeyi tanımlar.|**sınıfı**<br /><br /> **Sözleşmesi**|
|[&#60;güncelleştirme&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Gereklidir. Çözüm için güncelleştirmeleri yapılandırır.|**etkinletir**<br /><br /> **dolmadan**|
|[&#60;, Visual Studio 'da Office geliştirme&#62; öğe &#40;&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|İsteğe bağlı. Office çözümleri yüklendikten sonra çalıştırılan tüm dağıtım sonrası eylemlerini gruplandırır.|Hiçbiri|
|[&#60;Postaeylemi&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|İsteğe bağlı. Dağıtım sonrası eylemi tanımlar.|Hiçbiri|
|[&#60;postActionData&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|İsteğe bağlı. Dağıtım sonrası eylemi için verileri yapılandırır.|Hiçbiri|
|[ Visual Studio 'da Office geliştirme &#40;uygulama&#62; öğesi&#60;&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Gereklidir. Uygulamaya özgü bilgileri tek bir düğüme kaydırır.|Hiçbiri|
|[&#60;özelleştirmeler&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Gereklidir. Uygulamaya özgü tüm bilgileri ayrı bir ad alanında depolar.|Hiçbiri|
|[&#60;özelleştirme&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Gereklidir. Uygulama konağına özgü bilgileri ayrı bir ad alanında depolar.|**özniteliði**|
|[&#60;belge&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Yalnızca belge düzeyi çözümler için gereklidir. Özelleştirmeden özel bilgileri depolar.|**SolutionID**|
|[&#60;appAddin&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Yalnızca uygulama düzeyi çözümler için gereklidir. Özelleştirmeden özel bilgileri depolar.|**uygulama**<br /><br /> **loadBehavior**<br /><br /> **Işareti**|
|[&#60;friendlyName&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|İsteğe bağlı. , Yüklü VSTO eklentileri listesinde görünen VSTO eklentisinin adını depolar.|Hiçbiri|
|[&#60;Description&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Yalnızca VSTO eklentileri için gereklidir. Yüklü programlar listesinde görüntülenen açıklamayı depolar.|Hiçbiri|
|[&#60;FormRegion&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.|Hiçbiri|
|[&#60;formRegion&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Yalnızca form bölgelerini içeren Outlook VSTO eklentileri için gereklidir.|**Ad**|
|[&#60;vstoRuntime&#62; öğesi Visual Studio 'da Office geliştirme &#40;&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Gereklidir. Office çözümünün desteklediği, Office çalışma zamanı için Visual Studio Araçları belirli bir sürümünü açıklar.|**Yayın**<br /><br /> **Sürüm**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Açıklamalar
 Office çözümlerinde uygulama ve dağıtım bildirimlerini el ile düzenleyebilirsiniz. Daha sonra, Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe* ve *mageui.exe*) kullanarak uygulama ve dağıtım bildirimlerini yeniden imzalamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Dosya konumu
 Uygulama bildirimi, bir çözümün tek bir sürümüne özeldir. Bu nedenle, uygulama bildirimlerinin dağıtım bildirimlerinden ayrı olarak depolanması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sürüme özgü dosyaları Yayımla klasöründeki *uygulama dosyaları* alt dizininde ilişkili sürümden sonra adlı bir alt dizine koyar.

## <a name="file-name-syntax"></a>Dosya adı sözdizimi
 Uygulama bildirim dosyasının adı, **assemblyIdentity** öğesinde tanımlandığı şekilde uygulamanın tam adı ve uzantısı olmalıdır ve ardından *. manifest* uzantısını izler. Örneğin, *OutlookAddIn1.dll* özelleştirmeye başvuran bir uygulama bildirimi aşağıdaki dosya adı sözdizimini kullanır.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)