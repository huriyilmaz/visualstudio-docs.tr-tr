---
title: VSCT XML şeması Koşullu öznitelikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422169"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML Şeması Koşullu Öznitelikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Koşullu öznitelikler, tüm liste ve öğelere uygulanabilir. Mantıksal işleçler ve sembol genişletme ifadeleri true veya false olarak değerlendirilir. True ise, ilişkili liste veya öğe ortaya çıkan çıktıya dahil edilir.  
  
 Belirteç genişletmeleri, diğer belirteç genişletmeleri veya sabitlere karşı test edilebilir. Tanımlı () işlevi, bir değer olmasa bile belirli bir adın tanımlanıp tanımlanmadığını test etmek için kullanılır.  
  
 Bir koşul özniteliği bir listeye uygulandığında, koşul listedeki her alt öğeye uygulanır. Bir alt öğenin kendisi bir koşul özniteliği içeriyorsa, koşulu bir ve işlemi tarafından üst ifadeyle birleştirilir.  
  
 1, ' 1 ' ve ' true ' değerleri true olarak değerlendirilir ve 0, ' 0 ' ve ' false ' yanlış olarak değerlendirilir.  
  
## <a name="operators"></a>İşleçler  
 Aşağıdaki işleçler Koşullu ifadeleri değerlendirmek için kullanılabilir.  
  
|Operatör|Tanım|  
|--------------|----------------|  
|(,)|Gruplandırma|  
|!|Mantıksal değil|  
|\<, >, \<=, >=, ==, !=|İlişkisel ve eşitlik|  
|ve|Boole|  
|veya|Boole|  
  
## <a name="examples"></a>Örnekler  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
