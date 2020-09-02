---
title: Yalıtılmış Kabuk giriş noktası parametreleri (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825157"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Yalıtılmış Kabuk Giriş Noktası Parametreleri (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Shell tabanlı bir uygulama başlatıldığında, Visual Studio Kabuğu 'nun başlangıç giriş noktasını çağırır. Aşağıdaki ayarlar, kabuğun başlangıç giriş noktası çağrısında geçersiz kılınabilir. Her ayarın açıklaması için bkz [.. Pkgdef dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- Addınsallowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- Hidesolutionkavram  
  
- Newprojdlınstalınstaltemplateshdr  
  
- Newprojdlslntreenodetitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- Userfilesalt KlasörAdı  
  
- UserOptsFileExt  
  
  Visual Studio Kabuğu yalıtılmış şablonu *, SolutionName. cpp*adlı bir kaynak dosyası oluşturur, burada *SolutionName* uygulamanın çözüm adıdır. Bu dosya, uygulama için ana giriş noktasını tanımlar, _tWinMain işlevi. Bu işlev, kabuğun başlangıç giriş noktasını çağırır.  
  
  Uygulamanın başlatıldığı zaman bu ayarları değiştirerek uygulamanın davranışını değiştirebilirsiniz.  
  
## <a name="parameters"></a>Parametreler  
 Visual Studio Kabuğu 'nun başlangıç giriş noktası beş parametre tanımlar. İlk dört parametreyi değiştirmeyin. Beşinci parametre ayarları geçersiz kılma listesini alır. Kabuğun başlangıç giriş noktası, bir uygulamanın ana giriş noktasından çağrılır.  
  
 Kabuğun başlangıç giriş noktası aşağıdaki imzaya sahiptir.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Herhangi bir uygulama ayarını geçersiz kılmak istemiyorsanız, ayarlar geçersiz kılma parametresinin değerini boş bir işaretçi olarak bırakın.  
  
 Bir veya daha fazla ayarı geçersiz kılmak için, geçersiz kılınacak ayarları içeren bir Unicode dizesi geçirin. Dize, ad-değer çiftleri için noktalı virgülle ayrılmış bir listesidir. Her bir çift geçersiz kılınacak ayarın adını, ardından eşittir işareti (=) ve ardından ayara uygulanacak değeri içerir.  
  
> [!NOTE]
> Unicode dizelerinde boşluk eklemeyin.  
  
 Boole ayarları için aşağıdaki dizeler doğru değeri temsil eder; Tüm diğer dizeler yanlış değerini temsil eder. Bu dizeler büyük/küçük harfe duyarlıdır.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- evet  
  
## <a name="example"></a>Örnek  
 Eklentileri devre dışı bırakmak ve uygulamanız için varsayılan proje konumunu değiştirmek için, son parametreyi "Addınsallowed = false; DefaultProjectsLocation =%USERPROFILE%\temp" olarak ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yalıtılmış Kabuğu özelleştirme](../extensibility/customizing-the-isolated-shell.md)   
 [.Pkgdef Dosyaları](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
