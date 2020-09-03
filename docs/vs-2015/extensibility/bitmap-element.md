---
title: Bit eşlem öğesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184742"
---
# <a name="bitmap-element"></a>Bitmap Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bit eşlemi tanımlar. Bit eşlem bir kaynaktan ya da bir dosyadan yüklenir.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|guid|Gereklidir. GUID/ID komut tanımlayıcısının GUID 'SI.<br /><br /> Bit eşlemin GUID özniteliği herhangi bir VSPackage veya diğer komut grubuyla ilişkili değil.  Bit eşlem tanımının benzersiz olması ve herhangi bir amaçla kullanılmamalıdır.|  
|RESID|GUID/ID komut tanımlayıcısının KIMLIĞI. Resd ya da href özniteliği gereklidir.<br /><br /> Resd özniteliği, komut tablosu birleştirme sırasında yüklenecek bit eşlem şeridi belirleyen bir tamsayı kaynak KIMLIĞIDIR.  Komut tablosu yüklenirken, kaynak KIMLIĞI tarafından belirtilen bit eşlemler aynı modülün kaynağından yüklenir.|  
|usedList|Resd özniteliği mevcutsa gereklidir. Bit eşlem şeridinde kullanılabilir görüntüleri seçer.|  
|değerini|Bit eşlemin yolu. Resd ya da href özniteliği gereklidir.<br /><br /> Dahil edilen ikiliye gömülü olan belirtilen görüntü dosyası için ekleme yolu aranır.  Komut tablosu birleştirme sırasında görüntü kopyalanır ve ek kaynak araması veya yükleme gerekmez.  UsedList özniteliği yoksa, şerit 'teki tüm görüntüler kullanılabilir. **Note:**  Resimler,. bmp,. png ve. gif içeren birkaç biçimden birinde sağlanabilir.  Derleyicinin önceki sürümleri, kısmi saydamlık için alfa bilgilerine sahip 32 bit bit eşlem görüntülerini desteklemez. Bu sürümler için geçici çözüm. png biçimini kullanmaktır.|  
|Koşul|İsteğe bağlı. Bkz. [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Bitmaps Öğesi](../extensibility/bitmaps-element.md)|Bit eşlem öğelerini gruplandırır.|  
  
## <a name="example"></a>Örnek  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
