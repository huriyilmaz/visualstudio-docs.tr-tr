---
title: Derleme bilgileri Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661019"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Derleme bilgileri** iletişim kutusu [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , projenize otomatik olarak oluşturulan AssemblyInfo dosyasında depolanan genel derleme özniteliklerinin değerlerini belirtmek için kullanılır. **Çözüm Gezgini**, dosya Içindeki **projem** düğümünden bulunur [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (görüntülemek için **tüm dosyaları göster** ' e tıklayın); içindeki **Özellikler** altında bulunur [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Derleme öznitelikleri hakkında daha fazla bilgi için bkz. [öznitelikler](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Bu iletişim kutusuna erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesine tıklayın. **Uygulama** sayfasında, **derleme bilgileri** düğmesine tıklayın.

## <a name="uielement-list"></a>UIElement Listesi
 **Başlık** Bütünleştirilmiş kod bildirimi için bir başlık belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyTitleAttribute> .

 **Açıklama** Derleme bildirimi için isteğe bağlı bir açıklama belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyDescriptionAttribute> .

 **Şirket** Bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyCompanyAttribute> .

 **Ürün** Derleme bildirimi için bir ürün adı belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyProductAttribute> .

 **Telif hakkı** Derleme bildirimi için bir telif hakkı bildirimi belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyCopyrightAttribute> .

 **Ticari marka** Derleme bildirimi için bir ticari marka belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyTrademarkAttribute> .

 **Derleme sürümü** Derlemenin sürümünü belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyVersionAttribute> .

 **Dosya sürümü** Derleyiciye Win32 dosya sürümü kaynağı için belirli bir sürüm kullanmasını yönlendiren bir sürüm numarası belirtir. Öğesine karşılık gelir <xref:System.Reflection.AssemblyFileVersionAttribute> .

 **GUID** Derlemeyi tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. Öğesine karşılık gelir <xref:System.Guid> .

 **Nötr dil** Derlemenin desteklediği kültürü belirtir. Öğesine karşılık gelir <xref:System.Resources.NeutralResourcesLanguageAttribute> . Varsayılan değer **(yok)**.

 **DERLEMEYI com-görünür yap** Derlemedeki türlerin COM tarafından kullanılabilir olup olmayacağını belirtir. Öğesine karşılık gelir <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulama sayfası, proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md) [öznitelikleri](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
