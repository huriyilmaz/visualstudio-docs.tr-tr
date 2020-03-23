---
title: Oyununuzda veya Uygulamanızda 3B Varlıkları Kullanma
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d38f87970d5f9ff6d90befc61073cc4ed3d4ca92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589831"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Nasıl kullanılır: Oyununuzda veya uygulamanızda 3B varlıkları kullanın

Bu makalede, Visual Studio'nun 3B varlıkları işlemek ve bunları yapılarınıza dahil etmek için nasıl kullanabileceğiniz açıklanmaktadır.

Visual Studio'daki araçları 3B varlıklar oluşturmak için kullandıktan sonra, bir sonraki adım bunları uygulamanızda kullanmaktır. Ancak, bunları kullanabilmek için önce varlıklarınızın DirectX'in anlayabileceği bir biçime dönüştürülmesi gerekir. Visual Studio, varlıklarınızı dönüştürmenize yardımcı olmak için, üretebileceği her tür varlık için yapı özelleştirmeleri sağlar. Yapınızdaki varlıkları eklemek için tek yapmanız gereken, yapı özelleştirmelerini kullanacak, varlıkları projenize ekleyecek ve varlıkları doğru yapı özelleştirmesini kullanacak şekilde yapılandırmaktır. Bundan sonra, varlıkları uygulamanıza yükleyebilir ve directx kaynaklarını oluşturarak ve doldurarak bunları kullanabilirsiniz.

## <a name="configure-your-project"></a>Projenizi yapılandırın

3B varlıklarınızı yapınızın bir parçası olarak dağıtmadan önce Visual Studio'nun dağıtmak istediğiniz varlık türlerini bilmesi gerekiyor. Visual Studio zaten birçok yaygın dosya türleri hakkında bilir, ancak uygulamaların sadece belirli türleri 3D varlıkları kullanmak çünkü, Visual Studio bir proje dosyaları bu tür inşa edeceğini varsaymaz. Visual Studio'ya, uygulamanızın her varlık türü için sağlanan farklı dosya türlerini yararlı bir şekilde nasıl işleyebilirlerini söyleyen *yapı özelleştirmelerini*(Visual Studio'ya nasıl yararlı bir şekilde işlenirsiniz) kullanarak bu tür varlıkları kullandığını söyleyebilirsiniz. Bu özelleştirmeler proje başına uygulandığından, tek yapmanız gereken projenize uygun özelleştirmeleri eklemektir.

### <a name="to-add-the-build-customizations-to-your-project"></a>Yapı özelleştirmelerini projenize eklemek için

1. **Çözüm Gezgini'nde,** proje için kısayol menüsünü açın ve ardından **Bağımlılıklar** > **Oluşturma Özelleştirmeleri'ni**seçin.

   **Visual C++ Yapı Özelleştirmeler Dosyaları** iletişim kutusu görüntülenir.

2. **Kullanılabilir Yapı Özelleştirme Dosyaları**altında, aşağıdaki tabloda açıklandığı gibi, projenizde kullanmak istediğiniz varlık türlerine karşılık gelen onay kutularını seçin:

    |Varlık türü|Özelleştirme Adı Oluşturma|
    |----------------| - |
    |Dokular ve görüntüler|**ImageContentTask(.targets, .props)**|
    |3D Modeller|**MeshContentTask(.targets, .props)**|
    |Gölgelendiriciler|**ShaderGraphContentTask(.targets, .props)**|

3. **Tamam** düğmesini seçin.

## <a name="include-assets-in-your-build"></a>Yapınıza varlıkları ekleme

Artık projeniz kullanmak istediğiniz farklı türde 3B varlıkları bildiğine göre, bir sonraki adım hangi dosyaların 3B varlıklar olduğunu ve ne tür varlıklar olduğunu söylemektir.

### <a name="to-add-an-asset-to-your-build"></a>Yapınıza bir varlık eklemek için

1. **Çözüm Gezgini'nde,** projenizde, bir varlığın kısayol menüsünü açın ve ardından **Özellikler'i**seçin.

   Varlığın **Özellik Sayfası** iletişim kutusu görüntülenir.

2. **Yapılandırma** ve **Platform** özelliklerinin değişikliklerinizin uygulanmasını istediğiniz değerlere ayarlı olduğundan emin olun.

3. **Yapılandırma Özellikleri** **altında, Genel'i**seçin ve ardından özellik ızgarasında, **Genel** **altında, Öğe Türü** özelliğini uygun içerik ardışık öğe türüne ayarlayın. Örneğin, bir resim veya doku dosyası için **Görüntü İçerik Ardışık Alanı'nı**seçin.

    > [!IMPORTANT]
    > Varsayılan olarak, Visual Studio, Visual Studio'da yerleşik olan **Resim** öğesi türünü kullanarak birçok görüntü dosyası türünün kategorilere alınması gerektiğini varsayar. Bu nedenle, görüntü içeriği ardışık tarafından işlenmesini istediğiniz her görüntünün **Madde Türü** özelliğini değiştirmeniz gerekir. 3B modeller ve görsel gölgeli grafikler için diğer içerik boru hattı kaynak dosyaları doğru Öğe Türü için **varsayılan.**

4. **Tamam** düğmesini seçin.

Aşağıda üç içerik ardışık madde türleri ve bunların ilişkili kaynak ve çıktı dosya türleri verilmiştir.

|Madde Türü|Kaynak dosya türleri|Çıktı dosyası biçimi|
|---------------| - | - |
|**Görüntü İçerik Boru Hattı**|Taşınabilir Ağ Grafikleri (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Doğrudan Çekme Yüzeyi (*.dds*)<br /><br /> Grafik Değişim Biçimi (*.gif*)<br /><br /> Bitmap (*.bmp*, *.dib*)<br /><br /> Tagged Resim Dosyası Formatı (*.tif*, *.tiff*)<br /><br /> Targa (*.tga*)|DirectDraw Yüzeyi (*.dds*)|
|**Kafes İçerik Boru Hattı**|AutoDesk FBX Değişim Dosyası (*.fbx*)<br /><br /> Collada DAE Dosyası (*.dae*)<br /><br /> Wavefront OBJ Dosya (*.obj*)|3B örgü dosyası (*.cmo*)|
|**Gölgeli İçerik Boru Hattı**|Görsel Shader Grafiği (*.dgsl*)|Derlenmiş Shader Çıkışı (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Varlık içeriği boru hattı özelliklerini yapılandırma

Her varlık dosyasının içerik ardışık özelliklerini belirli bir şekilde oluşturulacak şekilde ayarlayabilirsiniz.

### <a name="to-configure-content-pipeline-properties"></a>İçerik ardışık yapı özelliklerini yapılandırmak için

1. **Çözüm Gezgini'nde,** projenizde varlık dosyasının kısayol menüsünü açın ve ardından **Özellikler'i**seçin.

   Varlığın **Özellik Sayfası** iletişim kutusu görüntülenir.

2. **Yapılandırma** ve **Platform** özelliklerinin, değişikliklerinizin uygulanmasını istediğiniz değerlere ayarlandığınızdan emin olun.

3. **Yapılandırma Özellikleri**altında, içerik ardışık dizi düğüm (örneğin, doku ve görüntü varlıkları için Görüntü **İçerik Ardışık Alanı)** seçin ve daha sonra özellik ızgarasında, özellikleri uygun değerlere ayarlayın. Örneğin, bir doku kıymetinin oluşturma zamanındaki mipmaps'i oluşturmak için **Mips oluştur** özelliğini **Evet**olarak ayarlayın.

4. **Tamam** düğmesini seçin.

### <a name="image-content-pipeline-configuration"></a>Görüntü içeriği ardışık yapı yapılandırması

Bir doku varlığı oluşturmak için görüntü içeriği pipeline aracını kullandığınızda, dokuyu çeşitli şekillerde sıkıştırabilir, MIP düzeylerinin oluşturma zamanında oluşturulup oluşturulmayacağını belirtebilir ve çıktı dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**Sıkıştır**|Çıktı dosyası için kullanılan sıkıştırma türünü belirtir.<br /><br /> Şu seçenekleri kullanabilirsiniz:<br /><br /> -   **Sıkıştırma Yok**<br />-   **BC1_UNORM sıkıştırma**<br />-   **BC1_UNORM_SRGB sıkıştırma**<br />-   **BC2_UNORM sıkıştırma**<br />-   **BC2_UNORM_SRGB sıkıştırma**<br />-   **BC3_UNORM sıkıştırma**<br />-   **BC3_UNORM_SRGB sıkıştırma**<br />-   **BC4_UNORM sıkıştırma**<br />-   **BC4_SNORM sıkıştırma**<br />-   **BC5_UNORM sıkıştırma**<br />-   **BC5_SNORM sıkıştırma**<br />-   **BC6H_UF16 sıkıştırma**<br />-   **BC6H_SF16 sıkıştırma**<br />-   **BC7_UNORM sıkıştırma**<br />-   **BC7_UNORM_SRGB sıkıştırma**<br /><br /> DirectX'in farklı sürümlerinde hangi sıkıştırma biçimlerinin desteklendiği hakkında bilgi için [DXGI için Programlama Kılavuzu'na](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews)bakın.|
|Önceden çarpılmış alfa biçimine dönüştürme|**Evet,** görüntüyü çıktı dosyasında önceden çarpılmış alfa biçimine dönüştürmek için; aksi takdirde, **Hayır**. Yalnızca çıktı dosyası değiştirilir, kaynak görüntü değişmez.|
|**Mips oluşturun**|**Evet,** inşa zamanında tam bir MIP zinciri oluşturmak ve çıktı dosyasına eklemek için; aksi takdirde, **Hayır**. **Hayır**ve kaynak dosya zaten bir mipmap zinciri içeriyorsa, çıktı dosyasında bir MIP zinciri olacaktır; aksi takdirde, çıktı dosyasında MIP zinciri olmaz.|
|**İçerik Çıktısı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıktı dosyasının dosya adı uzantısını değiştirmenin dosya biçimi üzerinde hiçbir etkisi yoktur.|

### <a name="mesh-content-pipeline-configuration"></a>Kafes içerik ardışık yapı yapılandırması

Bir kafes varlık oluşturmak için kafes içerik ardışık yapı aracını kullandığınızda, çıktı dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik Çıktısı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıktı dosyasının dosya adı uzantısını değiştirmenin dosya biçimi üzerinde hiçbir etkisi yoktur.|

### <a name="shader-content-pipeline-configuration"></a>Gölgeli içerik ardışık yapı yapılandırması

Gölgeli bir varlık oluşturmak için gölgeli içerik ardışık aracını kullandığınızda, çıktı dosyasının adını değiştirebilirsiniz.

|Özellik|Açıklama|
|--------------|-----------------|
|**İçerik Çıktısı**|Çıktı dosyasının adını belirtir. **Önemli:**  Çıktı dosyasının dosya adı uzantısını değiştirmenin dosya biçimi üzerinde hiçbir etkisi yoktur.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Çalışma zamanında 3B varlıkları yükleme ve kullanma

### <a name="use-textures-and-images"></a>Dokuları ve görüntüleri kullanma

Direct3D doku kaynakları oluşturmak için işlevler sağlar. Direct3D 11'de, D3DX11 yardımcı program kitaplığı doğrudan görüntü dosyalarından doku kaynakları ve kaynak görünümleri oluşturmak için ek işlevler sağlar. Direct3D 11'de doku kaynağı nın nasıl oluşturulacaaçık daha fazla bilgi için [Dokular'a](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures)bakın. Görüntü dosyasından doku kaynağı veya kaynak görünümü oluşturmak için D3DX11 kitaplığını nasıl kullanacağımız hakkında daha fazla bilgi için [bkz.](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to)

### <a name="use-3d-models"></a>3B modelleri kullanma

Direct3D 11, 3B modellerden kaynak oluşturmak için işlev sağlamaz. Bunun yerine, 3B model dosyasını okuyan ve 3B modeli ve modelin gerektirdiği kaynakları (örneğin dokular veya gölgeli) temsil eden tepe noktası ve dizin arabellekleri oluşturan kod yazmanız gerekir.

### <a name="use-shaders"></a>Gölgeli kullanma

Direct3D, gölgeli kaynaklar oluşturmak ve bunları programlanabilir grafik ardışık lığına bağlamak için işlevler sağlar. Direct3D'de gölgeli bir kaynağın nasıl oluşturulup boru hattına nasıl bağlanılabildiğini öğrenmek [için HLSL programlama kılavuzuna](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide)bakın.

Programlanabilir grafik ardışık lıkta, ardışık yolun her aşaması, ardışık yolun bir sonraki aşamasına anlayabileceği şekilde biçimlendirilmiş bir sonuç vermelidir. Shader Designer yalnızca piksel gölgeleyicileri oluşturabildiği için, aldığı verilerin beklediği biçimde olduğundan emin olmak uygulamanız kadardır. Piksel gölgeleyicisinden önce çeşitli programlanabilir gölgelenebilir aşamalar oluşur ve geometrik dönüşümler gerçekleştirir(tepe noktası gölgeleyici, gövde gölgeleyicisi, etki alanı gölgeleyicisi ve geometri gölgeleyicisi). Programlanabilir olmayan tessellation aşaması da piksel shader önce oluşur. Bu aşamalardan hangisi piksel gölgelendirmeden doğrudan önce gelirse gelsin, sonucunu bu biçimde vermelidir:

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

Gölgelendirmenizde kullandığınız Gölgeli Tasarımcı düğümlerine bağlı olarak, bu tanımlara göre biçimde ek veri sağlamanız da gerekebilir:

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
|[Nasıl yapılı: Mipmaps içeren bir doku dışa aktarma](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Önceden hesaplanmış mipmaps içeren bir doku dışa aktarmak için Görüntü İçerik Ardışık Alanı'nın nasıl kullanılacağını açıklar.|
|[Nasıl yapılır: Ön çarpımlı alfa kullanan dokuyu dışarı aktarma](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Önceden çarpılmış alfa değerleri içeren bir doku dışa aktarmak için Görüntü İçeriği Ardışık Alanı'nın nasıl kullanılacağını açıklar.|
|[Nasıl kullanılır: Direct2D veya JavaScript uygulamalarıyla kullanmak için bir doku dışa aktarma](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Direct2D veya JavaScript uygulamasında kullanılabilecek bir doku dışa aktarmak için Görüntü İçerik Ardışık Alanı'nın nasıl kullanılacağını açıklar.|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Visual Studio'nun dokular ve görüntüler, 3B modeller ve gölgeli leri içeren 3B varlıkları oluşturma ve işleme için sağladığı düzenleme araçlarını açıklar.|
|[Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)|Shader Designer'dan gölgeli nin nasıl dışa aktarılabildiğini açıklar.|
