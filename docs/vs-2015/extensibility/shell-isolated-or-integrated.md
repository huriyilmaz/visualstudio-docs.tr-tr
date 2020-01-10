---
title: Kabuk (yalıtılmış veya tümleşik) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850227"
---
# <a name="shell-isolated-or-integrated"></a>Kabuk (Yalıtılmış veya Tümleşik)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi Visual Studio tabanlı uygulamanızı tümleşik ya da yalıtılmış modda oluşturabilirsiniz. Tümleşik modda, uygulamanıza ek olarak birçok Visual Studio özelliği kullanılabilir. Yalıtılmış modda, kendi uzantınızla birlikte dağıtmak istediğiniz Visual Studio özelliklerinin bir alt kümesini seçebilirsiniz.  
  
## <a name="integrated-mode"></a>Tümleşik mod  
 Tümleşik mod, kullanıcılarınızın özel araçlarınızla birlikte standart Visual Studio özelliklerini kullanmasına olanak sağlar. Tümleşik Kabuk öncelikle programlama dillerini ve yazılım geliştirme araçlarını barındırmak için tasarlanmıştır.  
  
 Tümleşik kabukta oluşturulan özel araçlar, Visual Studio 'nun aynı bilgisayarda yüklü olan diğer herhangi bir sürümüyle otomatik olarak birleştirilir. Visual Studio 'nun zaten yüklü olmadığı durumlarda Visual Studio tümleşik kabuğu 'nun yeniden dağıtılabilir bir sürümünü sağlayabilirsiniz.  
  
 Visual Studio tümleşik kabuğun yeniden dağıtılabilir sürümü, programlama dillerini ve ilgili proje sistemlerini destekleyen özellikleri içermez.  
  
> [!NOTE]
> Visual Studio Kabuğu tümleşik modu, Visual Studio 'nun tüm sürümleriyle birlikte, Express sürümleri dışında yüklenebilir.  
  
 Daha fazla bilgi için bkz. [Visual Studio Kabuğu (tümleşik)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Yalıtılmış mod  
 Yalıtılmış mod, Visual Studio 'nun diğer sürümleriyle yan yana çalışan özel araçlar oluşturmanızı sağlar. Öncelikle, tüm standart Visual Studio özelliklerine bağlı kalmadan Visual Studio hizmetlerine erişebilen araçlara yöneliktir. Visual Studio yalıtılmış Kabuğu 'nda oluşturulan uygulamaların görünümünü özelleştirebilirsiniz. Uygulamanızla birlikte görüntülenmesini istemediğiniz özellikleri ve menü komut gruplarını kolayca kapatabilirsiniz.  
  
 Daha fazla bilgi için bkz. [Visual Studio yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Tümleşik veya yalıtılmış Kabuk uygulamanızı dağıtma  
 Tümleşik veya yalıtılmış Kabuk uygulamanızı dağıtmak için uygulamanızı, özel bir tümleşik veya yalıtılmış bir kabuk yeniden dağıtılabilir ve bir yükleme programını dahil etmeniz gerekir. Dağıtım ve yükleme hakkında daha fazla bilgi için bkz. [yalıtılmış Kabuk uygulamalarını dağıtma](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> Visual Studio tümleşik ve yalıtılmış kabukların [Son Kullanıcı Lisans Sözleşmesi (EULA)](https://www.visualstudio.com/support/legal/mt171552) , veri toplama (Bölüm 3) üzerinde bir bölüm içerir **. Veri**).  Uygulamanızda oluşturduğunuz tümleşik ya da yalıtılmış Kabuk yazılımlarının kullanıcılarından Microsoft tarafından toplanabilecek müşteri kullanım verilerini açıklar. Daha fazla bilgi için bkz. [Microsoft Visual Studio ürün ailesi gizlilik bildirimi](https://www.visualstudio.com/dn948229).  
> 
> Uygulamanız aracılığıyla müşterilerinizden ayrı kullanım verileri topluyorsanız, topladıklarınızın uygulamanız kullanıcılarına uygun bildirimi sağlamanız gerekir.  Visual Studio yazılım geliştirme seti lisansına göre yalıtılmış veya tümleşik kabuk yazılımını uygulamanızın bir parçası olarak dağıttığınızda, aşağıdakilerden birini eklemeniz gerekir:  
> 
> - Uygulama lisansınızın bir parçası olarak Son Kullanıcı Lisans Sözleşmesi  
> - Müşterilerinizin, Visual Studio ile tümleşik veya yalıtılmış Kabuğu en azından kabuk yazılımının Microsoft son kullanıcı lisans koşullarına kadar koruduğu koşulları kabul etmesi için kendi EULA 'Sı gerekir  
  
## <a name="additional-resources"></a>Ek Kaynaklar  
 Yeniden dağıtılabilir paketler hakkında daha fazla bilgi için bkz. [Visual Studio genişletilebilirlik indirmeleri](https://msdn.microsoft.com/vstudio/bb984878.aspx) Web sitesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
