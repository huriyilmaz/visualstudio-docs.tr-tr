---
title: Manifest to Code | Microsoft Docs
description: Visual Studio ımage hizmeti ile kullanmak üzere bir. ımagemanifest dosyası alan kod aracından bildirimi nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 17ecacea-397d-4a97-b003-01bd5d56e936
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 54bf0a3161fda86699b2bec07034b8732a099168
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626079"
---
# <a name="manifest-to-code"></a>Manifest to Code
Manifest to Code aracı, Visual Studio görüntü hizmeti için bir. ımagemanifest dosyası alan ve Visual Studio uzantıları için C++, C#, VB veya. vsct dosyalarındaki görüntü bildiriminin değerlerine başvurmak için bir sarmalayıcı dosyası ya da dosyaları oluşturan bir konsol uygulamasıdır. bu araç, Visual Studio görüntü hizmetinden doğrudan görüntü istemek için veya kod kendi kullanıcı arabirimini ve işlemesini karşılamıyorsa apı 'ler aracılığıyla bildirim değerlerini iletmek için kullanılabilecek sarmalayıcı dosyaları oluşturur.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Syntax**

 ManifestToCode/manifest: \<Image Manifest file> /Language: \<Code Language>\<Optional Args>

 **Bağımsız değişkenler**

|**Anahtar adı**|**Notlar**|**Gerekli veya Isteğe bağlı**|
|-|-|-|
|/MANIFEST|Kod sarmalayıcısı oluşturmak veya güncelleştirmek için kullanılacak görüntü bildiriminin yolu.|Gerekli|
|/Language|Kod sarmalayıcısı oluşturmak için kullanılacak dil.<br /><br /> Geçerli değerler: CPP, C++, CS, CSharp, C#, VB veya VSCT değerleri büyük/küçük harfe duyarsızdır.<br /><br /> VSCT Language seçeneği için/monikerClass,/classAccess ve/Namespace seçenekleri yok sayılır.|Gerekli|
|/ımageıdclass|Imageıdclass ve araç tarafından oluşturulan ilişkili dosya adı. C++ dil seçeneği için yalnızca. h dosyaları oluşturulur.<br /><br /> Varsayılan: \<Manifest Path> \Myımageıds.\<Lang Ext>|İsteğe Bağlı|
|/monikerClass|Araç tarafından oluşturulan monikerClass ve ilişkili dosyanın adı. C++ dil seçeneği için yalnızca. h dosyaları oluşturulur. Bu, VSCT dili için yoksayılır.<br /><br /> Varsayılan: \<Manifest Path> \MyMonikers.\<Lang Ext>|İsteğe Bağlı|
|/classAccess|Imageıdclass ve monikerClass için erişim değiştiricisi. Erişim değiştiricisinin verilen dil için geçerli olduğundan emin olun. Bu, VSCT dili seçeneği için yoksayılır.<br /><br /> Varsayılan: genel|İsteğe Bağlı|
|/Namespace|Kod sarmalayıcısı içinde tanımlanan ad alanı. Bu, VSCT dili seçeneği için yoksayılır. Seçilen dil seçeneğinden bağımsız olarak, '. ' veya ':: ' geçerli bir ad alanı ayırıcıları olmalıdır.<br /><br /> Varsayılan: myImages|İsteğe Bağlı|
|/noLogo|Bu bayrak ayarlandığında, ürün ve telif hakkı bilgilerinin yazdırılması durduruluyor.|İsteğe Bağlı|
|/?|Yardım bilgilerini yazdır.|İsteğe Bağlı|
|/help|Yardım bilgilerini yazdır.|İsteğe Bağlı|

 **Örnekler**

- ManifestToCode/manifest: D:\mymanifest.exe ımagemanifest/Language: CSharp

- ManifestToCode/manifest: D:\mymanifest.exe ımagemanifest/Language: C++/Namespace: My:: Namespace/ımageıdclass: Myımageıds/monikerClass: Mytakma ad/classAccess: arkadaş

- ManifestToCode/manifest: D:\mymanifest.exe ımagemanifest/Language: VSCT/ımageıdclass: Myımageıds

## <a name="notes"></a>Notlar

- Bu aracı, Manifest from Resources aracı tarafından oluşturulan görüntü bildirimleri ile kullanmanızı öneririz.

- Araç, kod sarmalayıcıları oluşturmak için yalnızca sembol girdilerine bakar. Görüntü bildiriminde sembol yoksa, oluşturulan kod sarmalayıcıları boş olur. Görüntü bildiriminde sembolleri kullanmayan bir görüntü veya resim kümesi varsa, bunlar kod sarmalayıcısından çıkarılır.

## <a name="sample-output"></a>Örnek çıktı
 **C# sarmalayıcıları**

 C# için bir çift basit görüntü KIMLIĞI ve resim bilinen adı sınıfları aşağıdaki koda benzer olacaktır:

```csharp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using System;

namespace MyImages
{
    public static class MyImageIds
    {
        public static readonly Guid AssetsGuid = new Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}");

        public const int MyImage1 = 0;
        public const int MyImage2 = 1;
    }
}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

using Microsoft.VisualStudio.Imaging.Interop;

namespace MyImages
{
    public static class MyMonikers
    {
        public static ImageMoniker MyImage1 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage1 }; } }
        public static ImageMoniker MyImage2 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage2 }; } }
    }
}
```

 **C++ sarmalayıcıları**

 C++ için bir çift basit görüntü KIMLIĞI ve resim bilinen adı sınıfları aşağıdaki koda benzer olacaktır:

```cpp
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include <guiddef.h>

namespace MyImages {

class MyImageIds {
public:

    static const GUID AssetsGuid;

    static const int MyImage1 = 0;
    static const int MyImage2 = 1;

};

__declspec(selectany) const GUID MyImageIds::AssetsGuid = {0x442d8739,0xefde,0x46a4,{0x8f,0x29,0xe3,0xa1,0xe5,0xe7,0xf8,0xb4}};

}
//-----------------------------------------------------------------------------
// <auto-generated>
//     This code was generated by the ManifestToCode tool.
//     Tool Version: 14.0.15198
// </auto-generated>
//-----------------------------------------------------------------------------

#pragma once

#include "ImageParameters140.h"
#include "MyImageIds.h"

namespace MyImages {

class MyMonikers {
public:

    static const ImageMoniker MyImage1;
    static const ImageMoniker MyImage2;

};

__declspec(selectany) const ImageMoniker MyMonikers::MyImage1 = { MyImageIds::AssetsGuid, MyImageIds::MyImage1 };
__declspec(selectany) const ImageMoniker MyMonikers::MyImage2 = { MyImageIds::AssetsGuid, MyImageIds::MyImage2 };

}
```

 **sarmalayıcılar Visual Basic**

 Visual Basic için bir çift basit görüntü kimliği ve resim bilinen adı sınıfları aşağıdaki koda benzer olacaktır:

```vb
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports System

Namespace MyImages

    Public Module MyImageIds

        Public Shared ReadOnly AssetsGuid As Guid = New Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}")

        Public Const MyImage1 As Integer = 0
        Public Const MyImage2 As Integer = 1

    End Module

End Namespace
' -----------------------------------------------------------------------------
'  <auto-generated>
'      This code was generated by the ManifestToCode tool.
'      Tool Version: 14.0.15198
'  </auto-generated>
' -----------------------------------------------------------------------------

Imports Microsoft.VisualStudio.Imaging.Interop

Namespace MyImages

    Public Module MyMonikers

        Public Readonly Property MyImage1
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage1}
            End Get
        End Property

        Public Readonly Property MyImage2
            Get
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage2}
            End Get
        End Property

    End Module

End Namespace
```

 **VSCT sarmalayıcısı**

 Bir. vsct dosyası için bir görüntü kimliği kümesi şuna benzer olacaktır:

```xml
<?xml version='1.0' encoding='utf-8'?>
<!--
- [auto-generated]
     This code was generated by the ManifestToCode tool.
     Tool Version: 14.0.15198
- [/auto-generated]
-->
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
  <Symbols>
    <GuidSymbol name="AssetsGuid" value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}">
      <IDSymbol name="MyImage1" value="0" />
      <IDSymbol name="MyImage2" value="1" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```
