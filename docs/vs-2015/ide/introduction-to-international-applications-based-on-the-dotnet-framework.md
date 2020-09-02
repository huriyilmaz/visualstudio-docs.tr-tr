---
title: .NET Framework göre uluslararası uygulamalara giriş | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d57cee8591196d12e51e58fb0e5e6a4a2cdf94a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848373"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>.NET Framework Tabanlı Uluslararası Uygulamalara Giriş
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

' De [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , dünya çapında kullanılabilir bir uygulama oluşturmak için iki bölüm vardır: Genelleştirme, farklı kültürlere uyarlanabilen uygulamaları tasarlama işlemi ve yerelleştirme, belirli bir kültür için kaynakları çevirme işlemi. Uluslararası bir hedef kitle için uygulama tasarlama hakkında genel bilgi için bkz. [Dünya çapında kullanılabilecek uygulamalar geliştirmek Için En Iyi uygulamalar](https://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Yerelleştirme modeli, uygulama kodu ve geri dönüş kaynakları içeren bir ana derlemeden ve uygulamanın ilk geliştirildiği dile ait dizeler, görüntüler ve diğer nesneler içerir. Her yerelleştirilmiş uygulamanın uydu derlemeleri veya yalnızca yerelleştirilmiş kaynakları içeren derlemeler olacaktır. Ana derleme her zaman geri dönüş kaynaklarını içerdiğinden, bir kaynak yerelleştirilmiş uydu derlemesinde bulunamazsa, <xref:System.Resources.ResourceManager> onu hiyerarşik bir şekilde yüklemeye çalışır ve sonuçta ana derlemede kaynağa geri düşerler. Kaynak geri dönüş sistemi, [Yerelleştirme Için kaynakların hiyerarşik kuruluşunda](../ide/hierarchical-organization-of-resources-for-localization.md)daha ayrıntılı olarak açıklanmıştır.

 Kullanarak göz önünde bulundurmanız gereken bir yerelleştirme kaynağı, tüm Microsoft yerelleştirilmiş ürünlerin sözlüğbir biridir. Bu CSV dosyasında 12.000 ' den fazla Ingilizce terim ve bu koşulların en fazla 59 farklı dilde olan çevirileri bulunur. Sözlük, [Microsoft terminoloji çevirileri](https://msdn.microsoft.com/goglobal/bb688105.aspx) Web sayfasında indirilebilir.

 Windows Forms uygulamalar için proje sistemi hem geri dönüş hem de istediğiniz her ek kullanıcı arabirimi kültürü için kaynak dosyaları oluşturabilir. Geri dönüş kaynak dosyası ana derlemede yerleşik olarak bulunur ve kültüre özgü kaynak dosyaları her bir kullanıcı arabirimi kültürü için bir tane olmak üzere uydu Derlemeleriyle yerleşik olarak bulunur. Bir proje oluşturduğunuzda, kaynak dosyaları Visual Studio XML biçiminden (. resx), daha sonra uydu derlemelerine gömülü bir ara ikili biçime (. resources) derlenir.

 Hem Windows Forms hem de Web Forms için proje sistemi, bir derleme kaynak dosyası şablonu kullanarak kaynak dosyaları oluşturmanızı, kaynaklara erişmeyi ve projenizi oluşturmanızı sağlar. Uydu derlemeleri ana derlemeyle birlikte oluşturulacaktır.

 Yerelleştirilmiş bir uygulama yürütüldüğünde, görünümü iki kültür değeri tarafından belirlenir. ( *Kültür* , kullanıcının dili, ortamı ve kültürel kuralları ile ilgili Kullanıcı tercihi bilgileri kümesidir.) UI kültürü ayarı hangi kaynakların yükleneceğini belirler. Kullanıcı arabirimi kültürü, `UICulture` Web.config dosya ve sayfa yönergelerinde ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> Visual Basic ya da Visual C# kodunda olarak ayarlanır. Kültür ayarı Tarih, sayı, para birimi vb. gibi değerlerin biçimlendirilmesini belirler. Kültür `Culture` Web.config dosya ve sayfa yönergelerinde, <xref:System.Globalization.CultureInfo.CurrentCulture%2A> Visual Basic veya Visual C# kodunda olarak ayarlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Globalization> <xref:System.Resources>
 Uygulamalar [güvenlik ve yerelleştirilmiş uydu derlemelerini](../ide/security-and-localized-satellite-assemblies.md) [Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)
