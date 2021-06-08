---
title: VSıX renk derleyicisi | Microsoft Docs
description: Visual Studio temalarının renklerini bir. pkgdef dosyasına bağlayan bir konsol uygulaması olan Visual Studio Uzantı rengi derleyicisi aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92914703ea4b293ac054c841251b37886bbc1d5a
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588468"
---
# <a name="vsix-color-compiler"></a>VSIX Renk Derleyicisi
Visual Studio Uzantı rengi derleyici aracı, var olan Visual Studio temaları için renkleri temsil eden bir .xml dosyası alan ve bu renklerin Visual Studio 'da kullanılabilmesi için bir. pkgdef dosyasına bağlayan bir konsol uygulamasıdır. .xml dosyalar arasındaki farkları karşılaştırmak kolaydır çünkü bu araç, kaynak denetimindeki özel renkleri yönetmek için yararlıdır. Ayrıca derleme ortamlarına, derleme çıkışının geçerli bir. pkgdef dosyası olması için de bağlanabilir.

 **Tema XML şeması**

 Tüm tema .xml dosyası şöyle görünür:

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

 \<Theme>Öğesi bir temanın tamamını tanımlar. Bir tema en az bir öğe içermelidir \<Category> . Tema öğeleri şöyle tanımlanır:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|Istenir Temanın adı|
|GUID|Istenir Temanın GUID 'SI (GUID biçimlendirmesine uymalıdır)|

 Visual Studio için özel renkler oluştururken, bu renklerin aşağıdaki Temalar için tanımlanması gerekir. Belirli bir tema için bir renk yoksa, Visual Studio açık temadaki eksik renkleri yüklemeye çalışır.

|**Tema adı**|**Tema GUID 'SI**|
|-|-|
|Açık|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Koyu|{1ded0138-47ce-435E-84ef-9ec1f439b749}|
|Mavi|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Yüksek Karşıtlık|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Kategori**

 \<Category>Öğesi, bir temadaki renklerin koleksiyonunu tanımlar. Kategori adları mantıksal gruplandırmaları sağlar ve mümkün olduğunca dar olarak tanımlanmalıdır. Kategori en az bir \<Color> öğe içermelidir. Kategori öğeleri şöyle tanımlanır:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|Istenir Kategorinin adı|
|GUID|Istenir Kategorinin GUID 'SI (GUID biçimlendirmesine uymalıdır)|

 **Renk**

 \<Color>Öğesi bir bileşen veya Kullanıcı arabirimi durumu için bir renk tanımlar. Bir renk için tercih edilen adlandırma şeması [UI türü] [State]. Gereksiz olduğu için "Color" sözcüğünü kullanmayın. Renk, öğe türünü ve durumları ya da rengin uygulanacağı "durumu" açıkça göstermelidir. Bir renk boş olmamalı ve bir ve öğelerinin bir veya her ikisini de içermelidir \<Background> \<Foreground> . Renk öğeleri şöyle tanımlanır:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Name|Istenir Rengin adı|

 **Arka plan ve/veya ön plan**

 \<Background>Ve \<Foreground> öğeleri bir kullanıcı arabirimi öğesinin arka plan veya ön planı için bir rengin değerini ve türünü tanımlar. Bu öğelerin alt öğesi yok.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|Istenir Rengin türü. Şunlardan biri olabilir:<br /><br /> *CT_INVALID:* Renk geçersiz veya ayarlı değil.<br /><br /> *CT_RAW:* Ham ARGB değeri.<br /><br /> *CT_COLORINDEX:* KULLANMAYıN.<br /><br /> *CT_SYSCOLOR:* Syscreng'ten bir Windows sistem rengi.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX bir Visual Studio rengi.<br /><br /> *CT_AUTOMATIC:* Otomatik renk.<br /><br /> *CT_TRACK_FOREGROUND:* KULLANMAYıN.<br /><br /> *CT_TRACK_BACKGROUND:* KULLANMAYıN.|
|Kaynak|Istenir Onaltılık renkle temsil edilen rengin değeri|

 __VSCOLORTYPE numaralandırması tarafından desteklenen tüm değerler, tür özniteliğinde şema tarafından desteklenir. Ancak, yalnızca CT_RAW ve CT_SYSCOLOR kullanmanızı öneririz.

 **Hepsi birlikte**

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

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Syntax**

 Valtcolorcompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Bağımsız değişkenler**

|**Anahtar adı**|**Notlar**|**Gerekli veya Isteğe bağlı**|
|-|-|-|
|Adlandırılmamış (.xml dosyası)|Bu ilk adlandırılmamış parametredir ve dönüştürülecek XML dosyasının yoludur.|Gerekli|
|Adlandırılmamış (. pkgdef dosyası)|Bu ikinci adlandırılmamış parametredir ve oluşturulan. pkgdef dosyası için çıkış yoludur.<br /><br /> Varsayılan: \<XML Filename> . pkgdef|İsteğe Bağlı|
|/noLogo|Bu bayrak ayarlandığında, ürün ve telif hakkı bilgilerinin yazdırılması durduruluyor.|İsteğe Bağlı|
|/?|Yardım bilgilerini yazdır.|İsteğe Bağlı|
|/help|Yardım bilgilerini yazdır.|İsteğe Bağlı|

 **Örnekler**

- Valtcolorcompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- Valtcolorcompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Notlar

- Bu araç, VC++ çalışma zamanının en son sürümünün yüklü olması gerekir.

- Yalnızca tek dosyalar de destekler. Klasör yolları aracılığıyla toplu dönüştürme desteklenmiyor.

- Araç şu içinde bulunabilir: `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Örnek çıktı
 Araç tarafından oluşturulan .pkgdef dosyası aşağıdaki anahtarlara benzer:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
