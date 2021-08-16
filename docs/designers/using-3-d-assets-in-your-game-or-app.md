---
title: Oyun veya Uygulamanıza 3D Varlık Kullanma
description: 3D varlıkları Visual Studio ve bunları derlemelere dahil etmek için Visual Studio kullanmayı öğrenin. Visual Studio, ürettiği her varlık için derleme özelleştirmeleri sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: e4b173542659197472bcf99844d749d6992849cbc8a84db257da26ef05415b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452972"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Nasıl yapılır: Oyununuzda veya uygulamanızda 3B varlıklar kullanma

Bu makalede, 3D varlıkları Visual Studio ve bunları derlemelerinize dahil etmek için Visual Studio'i nasıl kullanabileceğiniz açıklanmıştır.

3D varlık oluşturmak Visual Studio araçları kullandıktan sonra, bir sonraki adım bunları uygulamanıza kullanmaktır. Ancak, bunları kullanamadan önce varlıklarınızı DirectX'in an kullanabileceği bir biçime dönüştürmeniz gerekir. Varlıklarınızı dönüştürmenize yardımcı olmak Visual Studio, üretebilen her varlık için derleme özelleştirmeleri sağlar. Varlıkları derlemenize dahil etmek için tek gereken projenizi derleme özelleştirmelerini kullanmak üzere yapılandırmak, varlıkları projenize eklemek ve varlıkları doğru derleme özelleştirmesini kullanmak üzere yapılandırmaktır. Bundan sonra, diğer DirectX uygulamasında olduğu gibi DirectX kaynakları oluşturarak ve doldurarak varlıkları uygulamanıza yükp kullanabilirsiniz.

## <a name="configure-your-project"></a>Projenizi yapılandırma

Derlemenizin bir parçası olarak 3D varlıklarınızı dağıt Visual Studio dağıtmak istediğiniz varlık türleri hakkında bilginiz gerekir. Visual Studio dosya türleri hakkında zaten bilginiz vardır, ancak yalnızca belirli türlerde uygulamalar 3B varlıklar Visual Studio projenin bu tür dosyaları derlemesi varsaymaz. Her Visual Studio için sağlanan derleme özelleştirmelerini *(Visual Studio* farklı dosya türlerini yararlı bir şekilde işlemeyi söyleyin) kullanarak, uygulamanıza bu tür varlıkları kullandığını söylemek için kullanabilirsiniz. Bu özelleştirmeler proje başına uygulandığı için tek gereken projenize uygun özelleştirmeleri eklemektir.

### <a name="to-add-the-build-customizations-to-your-project"></a>Derleme özelleştirmelerini projenize eklemek için

1. Bu **Çözüm Gezgini** proje kısayol menüsünü açın ve ardından Bağımlılıkları Derleme **Özelleştirmeleri'ni**  >  **seçin.**

   Visual C++ **Özelleştirmeleri Dosyaları Oluşturma iletişim** kutusu görüntülenir.

2. Kullanılabilir **Derleme Özelleştirme Dosyaları** altında, aşağıdaki tabloda açıklandığı gibi projesinde kullanmak istediğiniz varlık türlerine karşılık gelen onay kutularını seçin:

    |Varlık türü|Derleme özelleştirme adı|
    |----------------| - |
    |Dokular ve görüntüler|**ImageContentTask(.targets, .props)**|
    |3D Modeller|**MeshContentTask(.targets, .props)**|
    |Gölgelendiriciler|**ShaderGraphContentTask(.targets, .props)**|

3. Tamam **düğmesini** seçin.

## <a name="include-assets-in-your-build"></a>Derlemenize varlıkları dahil etmek

Projeniz kullanmak istediğiniz farklı 3B varlık türleri hakkında bilgi edindi. Bir sonraki adım, 3B varlık olan dosyaları ve bunların varlık türleri hakkında bilgi edinebilirsiniz.

### <a name="to-add-an-asset-to-your-build"></a>Derlemenize varlık eklemek için

1. Bu **Çözüm Gezgini** projesinde bir varlığın kısayol menüsünü açın ve Özellikler'i **seçin.**

   Varlığın Özellik **Sayfası iletişim** kutusu görüntülenir.

2. Yapılandırma ve Platform **özelliklerinin,** **değişikliklerinizin** uygulamak istediğiniz değerlere ayarlanmış olduğundan emin olun.

3. Yapılandırma **Özellikleri altında** **Genel'i** seçin ve ardından özellik kılavuzunda, **Genel** altında Öğe Türü özelliğini **uygun** içerik işlem hattı öğe türü olarak ayarlayın. Örneğin, bir görüntü veya doku dosyası için Görüntü İçeriği İşlem **Hattı'ı seçin.**

    > [!IMPORTANT]
    > Varsayılan olarak, Visual Studio birçok görüntü dosyası türünün, yerleşik görüntü öğesi  türü kullanılarak kategorilere ayrılmış olduğu varsay Visual Studio. Bu nedenle, görüntü içeriği **işlem hattı** tarafından işlenmesini istediğiniz her görüntünün Öğe Türü özelliğini değiştirebilirsiniz. 3D modeller ve görsel gölgelendirici grafikleri için diğer içerik işlem hattı kaynak dosyaları varsayılan olarak doğru **Öğe Türü'ne sahiptir.**

4. Tamam **düğmesini** seçin.

Aşağıda, üç içerik işlem hattı öğesi türü ve bunların ilişkili kaynak ve çıkış dosyası türleri ve yer alan liste ve bilgiler yer amalıdır.

|Öğe Türü|Kaynak dosya türleri|Çıkış dosyası biçimi|
|---------------| - | - |
|**Görüntü İçeriği İşlem Hattı**|Taşınabilir Ağ Grafikleri (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Doğrudan Çizim Yüzeyi (*.dds*)<br /><br /> Grafik Değişim Biçimi (*.gif*)<br /><br /> Bit *eşlem (.bmp*, *.dib*)<br /><br /> Etiketli Görüntü Dosyası Biçimi (*.tif*, *.tiff*)<br /><br /> Targa (*.tga*)|DirectDraw Surface (*.dds*)|
|**Mesh İçerik İşlem Hattı**|AutoDesk FBX Değişim Dosyası (*.fbx*)<br /><br /> Collada DAE Dosyası (*.dae*)<br /><br /> Wavefront OBJ Dosyası (*.obj*)|3D mesh file (*.cmo*)|
|**Gölgelendirici İçerik İşlem Hattı**|Visual Shader Graph (*.dgsl*)|Derlenmiş Gölgelendirici Çıkışı (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Varlık içeriği işlem hattı özelliklerini yapılandırma

Her varlık dosyasının içerik işlem hattı özelliklerini, belirli bir şekilde olacak şekilde oluşturabilirsiniz.

### <a name="to-configure-content-pipeline-properties"></a>İçerik işlem hattı özelliklerini yapılandırmak için

1. Bu **Çözüm Gezgini** projesinde varlık dosyasının kısayol menüsünü açın ve Özellikler'i **seçin.**

   Varlığın Özellik **Sayfası iletişim** kutusu görüntülenir.

2. Yapılandırma ve Platform **özelliklerinin,** **değişikliklerinizin** uygulamak istediğiniz değerlere ayarlanmış olduğundan emin olun.

3. Yapılandırma **Özellikleri altında,** içerik işlem hattı düğümünü seçin (örneğin **doku** ve görüntü varlıkları için Görüntü İçeriği İşlem Hattı) ve ardından özellik kılavuzunda özellikleri uygun değerlere ayarlayın. Örneğin, derleme zamanında doku varlığı için mipmap'ler oluşturmak için, **Mips Oluştur** özelliğini Evet olarak **ayarlayın.**

4. Tamam **düğmesini** seçin.

### <a name="image-content-pipeline-configuration"></a>Görüntü içeriği işlem hattı yapılandırması

Doku varlığı oluşturmak için görüntü içeriği işlem hattı aracını kullanarak dokuyu çeşitli yollarla sıkıştırabilirsiniz, derleme zamanında MIP düzeylerinin oluşturulıp oluşturulmay gerektiğini belirtebilir ve çıkış dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**Sıkıştır**|Çıkış dosyası için kullanılan sıkıştırma türünü belirtir.<br /><br /> Şu seçenekler sağlanır:<br /><br /> -   **Sıkıştırma Yok**<br />-   **BC1_UNORM sıkıştırma**<br />-   **BC1_UNORM_SRGB sıkıştırma**<br />-   **BC2_UNORM sıkıştırma**<br />-   **BC2_UNORM_SRGB sıkıştırma**<br />-   **BC3_UNORM sıkıştırma**<br />-   **BC3_UNORM_SRGB sıkıştırma**<br />-   **BC4_UNORM sıkıştırma**<br />-   **BC4_SNORM sıkıştırma**<br />-   **BC5_UNORM sıkıştırma**<br />-   **BC5_SNORM sıkıştırma**<br />-   **BC6H_UF16 sıkıştırma**<br />-   **BC6H_SF16 sıkıştırma**<br />-   **BC7_UNORM sıkıştırma**<br />-   **BC7_UNORM_SRGB sıkıştırma**<br /><br /> DirectX'in farklı sürümlerinde desteklenen sıkıştırma biçimleri hakkında bilgi için bkz. [DXGI için Programlama Kılavuzu.](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews)|
|Önceden çarpılır alfa biçimine dönüştürme|**Çıktı** dosyasında görüntüyü önceden çarparak alfa biçimine dönüştürmek için evet; aksi takdirde, **Hayır.** Yalnızca çıkış dosyası değiştirilir, kaynak görüntü değiştirilmez.|
|**Mips Oluşturma**|**Derleme** zamanında tam bir MIP zinciri oluşturmak ve çıktı dosyasına eklemek için evet; aksi takdirde, **Hayır.** Hayır **ise** ve kaynak dosya zaten bir mipmap zinciri içeriyorsa, çıkış dosyasının bir MIP zinciri olur; aksi takdirde, çıkış dosyasında MIP zinciri olmaz.|
|**İçerik Çıkışı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıkış dosyasının dosya adı uzantısının değiştirilmesinin dosya biçimi üzerinde hiçbir etkisi yoktur.|

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

## <a name="load-and-use-3d-assets-at-run-time"></a>Çalışma zamanında 3B varlıkları yükleme ve kullanma

### <a name="use-textures-and-images"></a>Dokuları ve görüntüleri kullanma

Direct3D, doku kaynakları oluşturmak için işlevler sağlar. Direct3D 11 ' de, D3DX11 yardımcı program kitaplığı, doğrudan görüntü dosyalarından doku kaynakları ve kaynak görünümleri oluşturmak için ek işlevler sağlar. Direct3D 11 ' de doku kaynağı oluşturma hakkında daha fazla bilgi için bkz. [dokular](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Bir görüntü dosyasından doku kaynağı veya kaynak görünümü oluşturmak için D3DX11 kitaplığını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir dokuyu dosyadan doku başlatma](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to).

### <a name="use-3d-models"></a>3B modeller kullanma

Direct3D 11, 3D modellerden kaynak oluşturmak için işlevler sağlamaz. Bunun yerine, 3B model dosyasını okuyan ve 3B modeli ve modelin gerektirdiği tüm kaynakları (örneğin, dokular veya gölgelendiriciler) temsil eden köşe ve dizin arabellekleri oluşturan bir kod yazmanız gerekir.

### <a name="use-shaders"></a>Gölgelendiriciler kullanma

Direct3D, gölgelendirici kaynakları oluşturmak ve bunları programlanabilir grafik ardışık düzenine bağlamak için işlevler sağlar. Direct3D 'de gölgelendirici kaynağı oluşturma ve ardışık düzene bağlama hakkında daha fazla bilgi için bkz. [HLSL Için Programlama Kılavuzu](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide).

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

```hlsl
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
|[Nasıl yapılır: MIN haritaları içeren bir dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Önceden hesaplanan Mımage haritaları içeren bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeni 'nin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Ön çarpımlı alfa kullanan dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Ön çarpılmış Alfa değerlerini içeren bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeninin nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Direct2D veya JavaScript uygulamaları ile kullanmak için doku dışarı aktarma](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Direct2D veya JavaScript uygulamasında kullanılabilen bir dokuyu dışarı aktarmak için görüntü Içeriği ardışık düzeni 'nin nasıl kullanılacağını açıklar.|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|dokuları ve görüntüleri, 3b modelleri ve gölgelendiricileri içeren 3b varlıklar oluşturmak ve işlemek için Visual Studio sağladığı düzenleme araçlarını açıklar.|
|[Nasıl yapılır: gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)|Gölgelendirici tasarımcısından bir gölgelendiricinin nasıl dışarı aktarılacağını açıklar.|
