---
title: VSIX Renk Derleyicisi | Microsoft Docs
description: .pkgdef Visual Studio temalarında renkleri kapsayan bir konsol uygulaması olan Visual Studio Uzantısı Renk Derleyicisi aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1c724dae82bb8f7f05c83c96d1c331d72eac0abd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627261"
---
# <a name="vsix-color-compiler"></a>VSIX Renk Derleyicisi
Visual Studio Uzantısı Renk Derleyicisi aracı, mevcut Visual Studio temalarının renklerini temsil eden bir .xml dosyası alan ve bu renklerin Visual Studio'de kullanıla bir .pkgdef dosyasına kapatan bir konsol uygulamasıdır. Farklı dosyalar arasındaki farkları karşılaştırmak .xml, bu araç kaynak denetiminde özel renkleri yönetmek için kullanışlıdır. Derlemenin çıktısı geçerli bir .pkgdef dosyası olacak şekilde derleme ortamlarına da bağlanabilir.

 **Tema XML şeması**

 Dosyanın tam .xml şu şekildedir:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Tema**

 öğesi \<Theme> temayı tamamen tanımlar. Bir tema en az bir öğe \<Category> içermeli. Tema öğeleri şu şekilde tanımlanır:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|[Gerekli] Temanın adı|
|GUID|[Gerekli] Temanın GUID'si (GUID biçimlendirmesi ile eşleşmeli)|

 Visual Studio için özel renkler oluştururken, bu renklerin aşağıdaki temalar için tanımlanmalıdır. Belirli bir tema için renk yoksa, Visual Studio temadan eksik renkleri yükleme girişiminde bulun.

|**Tema adı**|**Tema GUID'si**|
|-|-|
|Açık|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Koyu|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Mavi|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Yüksek Karşıtlık|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategori**

 \<Category>öğesi, bir temada renk koleksiyonunu tanımlar. Kategori adları mantıksal gruplamalar sağlar ve mümkün olduğunca dar bir şekilde tanımlanmalıdır. Bir kategori en az bir öğe \<Color> içermeli. Kategori öğeleri şu şekilde tanımlanır:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|[Gerekli] Kategorinin adı|
|GUID|[Gerekli] Kategorinin GUID'si (GUID biçimlendirmesi ile eşleşmeli)|

 **Renk**

 öğesi, \<Color> bir bileşen veya kullanıcı arabiriminin durumu için bir renk tanımlar. Bir renk için tercih edilen adlandırma şeması [UI türü] [State] olur. Yedekli olduğu için "color" sözcüğü kullanma. Renk, öğe türünü ve rengin uygulanacak olduğu durumları veya "durum"ları net bir şekilde belirtmalıdır. Renk boş olamaz ve bir ve öğesinin bir veya her ikisini de \<Background> \<Foreground> içermesi gerekir. Renk öğeleri şu şekilde tanımlanır:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|[Gerekli] Rengin adı|

 **Arka plan ve/veya Ön Plan**

 ve öğeleri, bir ui öğesinin arka planı veya ön planı için bir rengin \<Background> \<Foreground> değerini ve türünü tanımlar. Bu öğelerin hiçbir yoktur.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|[Gerekli] Rengin türü. Şunlardan biri olabilir:<br /><br /> *CT_INVALID:* Renk geçersiz veya ayarlanmaz.<br /><br /> *CT_RAW:* Ham ARGB değeri.<br /><br /> *CT_COLORINDEX:* KULLANMAYIN.<br /><br /> *CT_SYSCOLOR:* SysColor Windows bir sistem rengi.<br /><br /> *CT_VSCOLOR:* Bir Visual Studio rengi __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Otomatik renk.<br /><br /> *CT_TRACK_FOREGROUND:* KULLANMAYIN.<br /><br /> *CT_TRACK_BACKGROUND:* KULLANMAYIN.|
|Kaynak|[Gerekli] Onaltılık olarak temsil edilen rengin değeri|

 Tür enumerasyonu __VSCOLORTYPE tüm değerler Tür özniteliğinde şema tarafından de destekler. Ancak, yalnızca kaynak ve CT_RAW CT_SYSCOLOR.

 **Hepsi birlikte**

 Bu, dosyada geçerli bir temanın .xml örneğidir:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Syntax**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Bağımsız değişkenler**

|**Anahtar adı**|**Notlar**|**Gerekli veya İsteğe Bağlı**|
|-|-|-|
|Adsız (.xml dosyası)|Bu, ilk adlandırlanmamış parametredir ve dönüştürülecek XML dosyasının yoludur.|Gerekli|
|Adsız (.pkgdef dosyası)|Bu, ikinci adlandırlanmamış parametredir ve oluşturulan .pkgdef dosyasının çıkış yoludur.<br /><br /> Varsayılan: \<XML Filename> .pkgdef|İsteğe Bağlı|
|/noLogo|Bu bayrağın ayarı ürün ve telif hakkı bilgilerini yazdırmayı durdurur.|İsteğe Bağlı|
|/?|Yardım bilgilerini yazdırma.|İsteğe Bağlı|
|/help|Yardım bilgilerini yazdırma.|İsteğe Bağlı|

 **Örnekler**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Notlar

- Bu araç, VC + + çalışma zamanının en son sürümünün yüklü olmasını gerektirir.

- Yalnızca tek dosyalar desteklenir. Klasör yolları aracılığıyla toplu dönüştürme desteklenmiyor.

- Araç şu şekilde bulunabilir `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Örnek çıktı
 Araç tarafından oluşturulan. pkgdef dosyası aşağıdaki anahtarlara benzer olacaktır:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
