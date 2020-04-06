---
title: VSIX Renk Derleyicisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703896"
---
# <a name="vsix-color-compiler"></a>VSIX Renk Derleyicisi
Visual Studio Extension Color Compiler aracı, mevcut Visual Studio temaları için renkleri temsil eden bir .xml dosyasını alan ve bu renklerin Visual Studio'da kullanılabilmesi için .pkgdef dosyasına coveryapan bir konsol uygulamasıdır. .xml dosyaları arasındaki farkları karşılaştırmak kolay olduğundan, bu araç kaynak denetiminde özel renkleri yönetmek için yararlıdır. Ayrıca yapının çıktısı geçerli bir .pkgdef dosyası olacak şekilde yapı ortamlarına bağlanabilir.

 **Tema XML şema**

 Tam bir tema .xml dosyası şuna benzer:

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

 \<Tema> öğesi tüm bir tema tanımlar. Bir tema en az \<bir Kategori> öğesi içermelidir. Tema öğeleri şu şekilde tanımlanır:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Adı|[Gerekli] Temanın adı|
|GUID|[Gerekli] Temanın GUID 'si (GUID biçimlendirmeile eşleşmelidir)|

 Visual Studio için özel renkler oluştururken, bu renklerin aşağıdaki temalar için tanımlanması gerekir. Belirli bir tema için renk yoksa, Visual Studio Eksik renkleri Işık temuzundan yüklemeye çalışır.

|||
|-|-|
|**Tema adı**|**Tema GUID**|
|Açık|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Koyu|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Mavi|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Yüksek Kontrast|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategori**

 \<Kategori> öğesi bir temadaki renk koleksiyonunu tanımlar. Kategori adları mantıksal gruplandırmalar sağlar ve mümkün olduğunca dar bir şekilde tanımlanmalıdır. Bir kategori en az \<bir Renk> öğesi içermelidir. Kategori öğeleri şu şekilde tanımlanır:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Adı|[Gerekli] Kategorinin adı|
|GUID|[Gerekli] Kategorinin GUID (GUID biçimlendirme eşleşmesi gerekir)|

 **Renk**

 \<Renk> öğesi, bir bileşen veya UI durumu için bir renk tanımlar. Bir renk için tercih edilen adlandırma düzeni [UI türü] [Durum] olur. Gereksiz olduğu için "renk" sözcüğü kullanmayın. Renk, öğe türünü ve durumları veya rengin uygulanacağı "durum" öğesini açıkça belirtmelidir. Bir renk boş olmamalı ve arka \<plan> ve \<Foreground> öğesinden birini veya her ikisini içermelidir. Renk öğeleri şu şekilde tanımlanır:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Adı|[Gerekli] Rengin adı|

 **Arka plan ve/veya Ön Plan**

 \<Arka Plan \<> ve Foreground> öğeleri bir rengin değerini ve türünü bir UI öğesinin arka planı veya ön planı için tanımlar. Bu elementlerin çocuğu yok.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Tür|[Gerekli] Rengin türü. Aşağıdakilerden biri olabilir:<br /><br /> *CT_INVALID:* Renk geçersiz veya ayarlı değil.<br /><br /> *CT_RAW:* Ham ARGB değeri.<br /><br /> *CT_COLORINDEX:* KULLANMAYıN.<br /><br /> *CT_SYSCOLOR:* SysColor bir Windows sistem rengi.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX'dan görsel stüdyo rengi.<br /><br /> *CT_AUTOMATIC:* Otomatik renk.<br /><br /> *CT_TRACK_FOREGROUND:* KULLANMAYıN.<br /><br /> *CT_TRACK_BACKGROUND:* KULLANMAYıN.|
|Kaynak|[Gerekli] Hexadecimal temsil edilen rengin değeri|

 __VSCOLORTYPE numaralandırma tarafından desteklenen tüm değerler, Tür özniteliğindeki şema tarafından desteklenir. Ancak, yalnızca CT_RAW ve CT_SYSCOLOR kullanmanızı öneririz.

 **Hep birlikte**

 Bu, geçerli bir tema .xml dosyasının basit bir örneğidir:

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

## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır?
 **Sözdizimi**

 VsixColorCompiler \<XML \<dosya> PkgDef dosyası isteğe bağlı Args>> \<

 **Bağımsız Değişkenler**

||||
|-|-|-|
|**Anahtar adı**|**Notlar**|**Gerekli veya İsteğe Bağlı**|
|Adsız (.xml dosyası)|Bu, ilk adlanmayan parametredir ve XML dosyasına dönüştürme yoludur.|Gerekli|
|İsimsiz (.pkgdef dosyası)|Bu ikinci adsız parametredir ve oluşturulan .pkgdef dosyasının çıktı yoludur.<br /><br /> Varsayılan: \<XML Dosya Adı>.pkgdef|İsteğe bağlı|
|/noLogo|Bu bayrağı ayarlamak, ürün ve telif hakkı bilgilerinin yazdırılmalarını durdurur.|İsteğe bağlı|
|/?|Yardım bilgilerini yazdırın.|İsteğe bağlı|
|/help|Yardım bilgilerini yazdırın.|İsteğe bağlı|

 **Örnekler**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Notlar

- Bu araç, VC++ çalışma zamanının en son sürümünün yüklenmesini gerektirir.

- Yalnızca tek dosyalar desteklenir. Klasör yolları üzerinden toplu dönüştürme desteklenmez.

## <a name="sample-output"></a>Örnek çıktı
 Araç tarafından oluşturulan .pkgdef dosyası aşağıdaki tuşlara benzer olacaktır:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
