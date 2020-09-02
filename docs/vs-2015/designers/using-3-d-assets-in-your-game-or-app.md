---
title: Oyununuzda veya uygulamanızda 3-b varlıkları kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f290c68933a71f40899ce454eb6ba788ef31a56f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846496"
---
# <a name="using-3-d-assets-in-your-game-or-app"></a>Oyunlarda veya Uygulamalarda 3B Varlıklar Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu makalede, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 3-b varlıkları işlemek ve bunları derlemelerinize eklemek için nasıl kullanabileceğiniz açıklanır.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]3-b varlıkları oluşturmak için içindeki araçları kullandıktan sonra, bir sonraki adım bunları uygulamanızda kullanmaktır. Ancak bunları kullanabilmeniz için, varlıklarınızın DirectX 'in anlayabilmesi için bir biçime dönüştürülmesi gerekir. Varlıklarınızı dönüştürmenizi kolaylaştırmak için, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] üretebileceğini her bir varlık türü için derleme özelleştirmeleri sağlar. Derlemenize varlıkları dahil etmek için tüm yapmanız gerekir derleme özelleştirmelerini kullanmak için projenizi yapılandırmak, varlıkları projenize eklemek ve doğru yapı özelleştirmesini kullanmak için varlıkları yapılandırmak. Bundan sonra, varlıkları uygulamanıza yükleyebilir ve diğer herhangi bir DirectX uygulamasında olduğu gibi DirectX kaynaklarını oluşturarak ve doldurarak kullanabilirsiniz.

## <a name="configuring-your-project"></a>Projenizi yapılandırma
 Derlemenize bir parçası olarak 3-b varlıklarınızı dağıtabilmeniz için önce, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dağıtmak istediğiniz varlık türleri hakkında bilgi sahibi olmanız gerekir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birçok ortak dosya türünü zaten biliyor, ancak yalnızca belirli türde uygulamalar 3-b varlıkları kullandığından, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projenin bu dosya türlerini sağladığını varsaymaz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Uygulamanızın, *build customizations* [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] her varlık türü için sunulan yapı özelleştirmelerini (farklı dosya türlerini kullanışlı bir şekilde nasıl işleyeceğini söyleyen dosyalar) kullanarak bu varlık türlerini kullandığını söyleyebilirsiniz. Bu özelleştirmeler proje başına temelinde uygulandığından, tüm yapmanız gereken, projenize uygun özelleştirmeler eklemektir.

#### <a name="to-add-the-build-customizations-to-your-project"></a>Projenize yapı özelleştirmeleri eklemek için

1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **yapı bağımlılıkları**, **yapı özelleştirmeleri**' ni seçin. **Visual C++ yapı özelleştirmeleri dosyaları** iletişim kutusu görüntülenir.

2. **Kullanılabilir yapı özelleştirmesi dosyaları**altında, projenizde kullanmak istediğiniz varlık türlerine karşılık gelen onay kutularını, bu tabloda açıklandığı gibi seçin:

    |Varlık türü|Yapı özelleştirmesi adı|
    |----------------|------------------------------|
    |Dokular ve görüntüler|**ImageContentTask (. targets,. props)**|
    |3-b modeller|**MeshContentTask (. targets,. props)**|
    |Gölgelendiriciler|**ShaderGraphContentTask (. targets,. props)**|

3. **Tamam** düğmesini seçin.

## <a name="including-assets-in-your-build"></a>Derlemenize varlıklar ekleme
 Artık projeniz, kullanmak istediğiniz farklı 3-b varlık türlerini öğrendiğinden, bir sonraki adım, hangi dosyaların 3-b varlık olduğunu ve hangi tür varlıkların olduğunu söyleyecektir.

#### <a name="to-add-an-asset-to-your-build"></a>Derlemenize bir varlık eklemek için

1. **Çözüm Gezgini**, projenizde bir varlığın kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Varlığın **özellik sayfası** iletişim kutusu görüntülenir.

2. **Yapılandırma** ve **Platform** özelliklerinin, değişikliklerinizin uygulanmasını istediğiniz değerlere ayarlandığından emin olun.

3. **Yapılandırma özellikleri**' nin altında **genel**' i seçin ve sonra özellik kılavuzunda, **genel**altında, **öğe türü** özelliğini uygun içerik ardışık düzen öğe türü olarak ayarlayın. Örneğin, bir görüntü veya doku dosyası için **görüntü içeriği Işlem hattı**' nı seçin.

   > [!IMPORTANT]
   > Varsayılan olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] birçok görüntü dosyası türünün, içinde yerleşik olarak bulunan **görüntü** öğesi türü kullanılarak kategorize olması gerektiğini varsayar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu nedenle, görüntü içeriği ardışık düzeni tarafından işlenmesini istediğiniz her bir görüntünün **öğe türü** özelliğini değiştirmeniz gerekir. 3-b modeller ve Visual gölgelendirici grafik için diğer içerik ardışık düzen kaynak dosyalarının doğru **öğe türü**için varsayılan türleri.

4. **Tamam** düğmesini seçin.

   Üç içerik ardışık düzen öğe türü ve bunların ilişkili kaynak ve çıkış dosyası türleri aşağıda verilmiştir.

|Öğe türü|Kaynak dosya türleri|Çıkış dosyası biçimi|
|---------------|-----------------------|------------------------|
|**Görüntü Içeriği ardışık düzeni**|Taşınabilir Ağ Grafikleri (. png)<br /><br /> JPEG (. jpg,. jpeg,. jpe,. JI)<br /><br /> Doğrudan çizim yüzeyi (. DDS)<br /><br /> Grafik Değişim Biçimi (. gif)<br /><br /> Bit eşlem (. bmp,. dib)<br /><br /> Etiketli resim dosyası biçimi (. tif,. tiff)<br /><br /> Targa (. TGA)|DirectDraw yüzeyi (. DDS)|
|**Kafes Içerik ardışık düzeni**|AutoDesk FBX değişim dosyası (. fbx)<br /><br /> Collada Dade dosyası (. Dade)<br /><br /> Wavefront OBJ dosyası (. obj)|3-b ağ dosyası (. CMO)|
|**Gölgelendirici Içerik ardışık düzeni**|Görsel Gölgelendirici Grafiği (. dgsl)|Derlenen gölgelendirici çıkışı (. CSO)|

## <a name="configuring-asset-content-pipeline-properties"></a>Varlık içeriği ardışık düzen özelliklerini yapılandırma
 Her bir varlık dosyasının içerik ardışık düzen özelliklerini belirli bir şekilde oluşturulacak şekilde ayarlayabilirsiniz.

#### <a name="to-configure-content-pipeline-properties"></a>İçerik ardışık düzen özelliklerini yapılandırmak için

1. **Çözüm Gezgini**, projenizde varlık dosyasının kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Varlığın **özellik sayfası** iletişim kutusu görüntülenir.

2. **Yapılandırma** ve **Platform** özelliklerinin, değişikliklerinizin uygulanmasını istediğiniz değerlere ayarlandığından emin olun.

3. **Yapılandırma özellikleri**altında, içerik ardışık düzeni düğümünü seçin — örneğin, doku ve görüntü varlıkları Için **görüntü içeriği işlem hattı** — ve sonra özellik kılavuzunda, özellikleri uygun değerlere ayarlayın. Örneğin, derleme zamanında bir doku varlığı için mı haritaları oluşturmak için, **MIPS oluştur** özelliğini **Evet**olarak ayarlayın.

4. **Tamam** düğmesini seçin.

### <a name="image-content-pipeline-configuration"></a>Görüntü içeriği ardışık düzen yapılandırması
 Bir doku varlığı oluşturmak için görüntü içeriği ardışık düzen aracını kullandığınızda, dokuyu çeşitli yollarla sıkıştırabilir, MıP düzeylerinin derleme zamanında oluşturulup oluşturulmayacağını belirtebilir ve çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**Madı**|Çıktı dosyası için kullanılan sıkıştırma türünü belirtir.<br /><br /> Şu seçenekleri kullanabilirsiniz:<br /><br /> -   **Sıkıştırma yok**<br />-   **BC1_UNORM sıkıştırma**<br />-   **BC1_UNORM_SRGB sıkıştırma**<br />-   **BC2_UNORM sıkıştırma**<br />-   **BC2_UNORM_SRGB sıkıştırma**<br />-   **BC3_UNORM sıkıştırma**<br />-   **BC3_UNORM_SRGB sıkıştırma**<br />-   **BC4_UNORM sıkıştırma**<br />-   **BC4_SNORM sıkıştırma**<br />-   **BC5_UNORM sıkıştırma**<br />-   **BC5_SNORM sıkıştırma**<br />-   **BC6H_UF16 sıkıştırma**<br />-   **BC6H_SF16 sıkıştırma**<br />-   **BC7_UNORM sıkıştırma**<br />-   **BC7_UNORM_SRGB sıkıştırma**<br /><br /> DirectX 'in farklı sürümlerinde hangi sıkıştırma biçimlerinin desteklendiği hakkında bilgi için bkz. [DXGı Için Programlama Kılavuzu](https://msdn.microsoft.com/library/windows/desktop/bb219822(v=vs.85).aspx).|
|Önceden çoğaltılmış alfa biçimine Dönüştür|**Evet** , görüntüyü çıkış dosyasında önceden çarpılan Alfa biçimine dönüştürmek için. Aksi takdirde, **Hayır**. Yalnızca çıkış dosyası değiştirildiğinde, kaynak görüntü değiştirilmez.|
|**MIPS oluştur**|Derleme zamanında tam MıP zinciri oluşturmak ve bunu çıkış dosyasına dahil etmek için **Evet** ; Aksi takdirde, **Hayır**. **Hayır**ise ve kaynak dosya zaten bir mipmap zinciri içeriyorsa, çıkış dosyası bir MIP zincirine sahip olur; Aksi takdirde, çıkış dosyası MıP zincirine sahip olmaz.|
|**İçerik çıkışı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıkış dosyasının dosya adı uzantısının değiştirilmesinin dosya biçimi üzerinde hiçbir etkisi yoktur.|

### <a name="mesh-content-pipeline-configuration"></a>Kafes içerik ardışık düzen yapılandırması
 Bir kafes varlığı oluşturmak için kafes içerik ardışık düzen aracını kullandığınızda, çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik çıkışı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıkış dosyasının dosya adı uzantısının değiştirilmesinin dosya biçimi üzerinde hiçbir etkisi yoktur.|

### <a name="shader-content-pipeline-configuration"></a>Gölgelendirici içerik ardışık düzen yapılandırması
 Gölgelendirici varlığı oluşturmak için gölgelendirici içerik ardışık düzen aracını kullandığınızda, çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik çıkışı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıkış dosyasının dosya adı uzantısının değiştirilmesinin dosya biçimi üzerinde hiçbir etkisi yoktur.|

## <a name="loading-and-using-3-d-assets-at-run-time"></a>Çalışma zamanında 3-b varlıklarını yükleme ve kullanma

### <a name="using-textures-and-images"></a>Dokuları ve görüntüleri kullanma
 Direct3D, doku kaynakları oluşturmak için işlevler sağlar. Direct3D 11 ' de, D3DX11 yardımcı program kitaplığı, doğrudan görüntü dosyalarından doku kaynakları ve kaynak görünümleri oluşturmak için ek işlevler sağlar. Direct3D 11 ' de doku kaynağı oluşturma hakkında daha fazla bilgi için bkz. [dokular](https://msdn.microsoft.com/library/windows/desktop/ff476902(v=vs.85).aspx). Bir görüntü dosyasından doku kaynağı veya kaynak görünümü oluşturmak için D3DX11 kitaplığını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir dokuyu dosyadan doku başlatma](https://msdn.microsoft.com/library/windows/desktop/ff476904(v=vs.85).aspx).

### <a name="using-3-d-models"></a>3-b modeller kullanma
 Direct3D 11, 3-b modellerinden kaynak oluşturmak için işlevler sağlamaz. Bunun yerine, 3-D model dosyasını okuyan ve 3B modeli ve modelin gerektirdiği tüm kaynakları (örneğin, dokular veya gölgelendiriciler) temsil eden köşe ve dizin arabellekleri oluşturan bir kod yazmanız gerekir.

### <a name="using-shaders"></a>Gölgelendiriciler kullanma
 Direct3D, gölgelendirici kaynakları oluşturmak ve bunları programlanabilir grafik ardışık düzenine bağlamak için işlevler sağlar. Direct3D 'de gölgelendirici kaynağı oluşturma ve ardışık düzene bağlama hakkında daha fazla bilgi için bkz. [HLSL Için Programlama Kılavuzu](https://msdn.microsoft.com/library/windows/desktop/bb509635(v=vs.85).aspx).

 Programlanabilir grafik ardışık düzeninde, işlem hattının her bir aşaması, anlanabilir bir şekilde biçimlendirilen bir sonuç olan işlem hattının sonraki aşamasına vermelidir. Gölgelendirici Tasarımcısı yalnızca Piksel gölgelendiricileri oluşturabileceğinden, bu, aldığı verilerin beklediği biçimde olduğundan emin olmak için uygulamanıza ait olduğu anlamına gelir. Birkaç programlanabilir gölgelendirici aşaması, piksel gölgelendiriciden önce oluşur ve geometrik dönüşümler, köşe gölgelendiricisi, kabuk gölgelendiricisi, etki alanı gölgelendiricisi ve geometri gölgelendirici gerçekleştirir. Programlanabilir olmayan mozaik döşeme aşaması, piksel gölgelendiriciden önce de gerçekleşir. Bu aşamaların ne kadar doğrudan piksel gölgelendiricisinin önünde olduğuna bakılmaksızın, bunun sonucunu bu biçimde vermelidir:

```hlsl

struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

 Gölgelendiricide kullandığınız gölgelendirici tasarımcı düğümlerine bağlı olarak, bu tanımlara göre biçimdeki ek verileri de sağlamanız gerekebilir:

```

Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: Mipmap'leri İçeren Dokuyu Dışa Aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Önceden hesaplanan Mımage haritaları içeren bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeni 'nin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: ön çarpılmış Alpha içeren bir dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Ön çarpılmış Alfa değerlerini içeren bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeninin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Direct2D veya JavaScipt uygulamalarıyla kullanmak için bir dokuyu dışarı aktarma](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Direct2D veya JavaScript uygulamasında kullanılabilen bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeni 'nin nasıl kullanılacağını açıklar.|
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Visual Studio 'Nun dokuları ve görüntüleri, 3-b modelleri ve gölgelendiricileri içeren 3-b varlıkları oluşturmak ve işlemek için sağladığı düzenleme araçlarını açıklar.|
|[Nasıl Yapılır: Gölgelendiriciyi Dışarı Aktarma](../designers/how-to-export-a-shader.md)|Gölgelendirici tasarımcısından bir gölgelendiricinin nasıl dışarı aktarılacağını açıklar.|
