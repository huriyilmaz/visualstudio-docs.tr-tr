---
title: Eski API 'YI kullanarak bir dil hizmeti bağlamı sağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193876"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Dil Hizmeti Bağlamı Sağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dil hizmetinin çekirdek düzenleyiciyi kullanarak Kullanıcı bağlamı sağlaması için iki seçenek vardır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] : metin işaretçisi bağlamı sağlama veya tüm kullanıcı bağlamını sağlama. Aralarında aralarındaki farklar burada özetlenmiştir.  
  
 Kendi düzenleyicinize bağlı bir dil hizmetine bağlam sağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: düzenleyiciler Için bağlam sağlama](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Düzenleyiciye metin Işaretçisi bağlamı sağlama  
 Çekirdek düzenleyicideki metin işaretçileriyle belirtilen derleyici hataları için bağlam sağlamak üzere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> arabirimini uygulayın. Bu senaryoda, dil hizmeti bağlamı yalnızca imleç metin işaretçisi üzerinde olduğunda sağlar. Bu, düzenleyicinin anahtar sözcüğünü bir öznitelik olmadan **dinamik yardım** penceresine sağlamasına izin verir.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Tüm kullanıcı bağlamını düzenleyiciye sağlama  
 Bir dil hizmeti oluşturuyorsanız ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çekirdek düzenleyiciyi kullanıyorsanız, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Dil hizmetiniz için bağlam sağlamak üzere arabirimi uygulayabilirsiniz.  
  
 Uygulamasının uygulanması için, bağlam `IVsLanguageContextProvider` çantasından sorumlu bir içerik paketi (koleksiyon) düzenleyiciye iliştirilir. **Dinamik yardım** penceresi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> Bu bağlam çantasında ara 'yı boş zamanlı olarak çağırdığında, içerik paketi bir güncelleştirme için düzenleyiciyi sorgular. Daha sonra düzenleyici, dil hizmetine düzenleyiciyi güncelleştirmesi gerektiğini bildirir ve bağlam çantasına bir işaretçi geçirir. Bu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> yöntemi düzenleyiciden dil hizmetine çağırarak yapılır. Dil hizmeti, bağlam çantasına yönelik işaretçiyi kullanarak artık öznitelik ve anahtar sözcükler ekleyebilir ve kaldırabilir. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Uygulamak için iki farklı yol vardır `IVsLanguageContextProvider` :  
  
- Bağlam çantasına bir anahtar sözcük sağlayın  
  
   Bağlam paketini güncelleştirmek için düzenleyici çağrıldığında, uygun anahtar kelimeleri ve öznitelikleri geçirin ve ardından döndürün `S_OK` . Bu dönüş değeri, düzenleyicide bağlam çantasında anahtar sözcüğü sağlamak yerine anahtar sözcüğünü ve öznitelik bağlamını korumasını ister.  
  
- İmleç içindeki anahtar sözcükten anahtar sözcüğü al  
  
   Bağlam paketini güncelleştirmek için düzenleyici çağrıldığında, uygun öznitelikleri geçirin ve ardından döndürün `E_FAIL` . Bu dönüş değeri, düzenleyiciye bağlam çantasında öznitelerinizi korumasını söyler, ancak içerik paketini imlecin bulunduğu anahtar sözcükle güncelleştirir.  
  
  Aşağıdaki diyagramda, uygulayan bir dil hizmeti için bağlamın nasıl sağlandığı gösterilmektedir `IVsLanguageContextProvider` .  
  
  ![LangServiceImplementation2 grafiği](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Dil hizmeti bağlamı  
  
  Diyagramda görebileceğiniz gibi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çekirdek metin düzenleyicisine eklenmiş bir içerik paketi vardır. Bu bağlam paketi üç ayrı alt bağlam çantasına işaret eder: dil hizmeti, varsayılan düzenleyici ve metin işaretçisi. Dil hizmeti ve metin işaretçisi alt bağlam paketleri, arabirim uygulanırsa dil hizmetinin özniteliklerini ve anahtar sözcüklerini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> ve arabirim uygulanmışsa Metin işaretleyicilerini içerir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> . Bu arabirimlerden birini gerçekleştirmeyin, düzenleyici varsayılan düzenleyici alt bağlam çantasında imlecin anahtar sözcüğü için bağlam sağlar.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Düzenleyiciler ve tasarımcılar için bağlam yönergeleri  
 Tasarımcılar ve düzenleyiciler, düzenleyici veya tasarımcı penceresi için genel bir anahtar sözcük sağlamalıdır. Bu, bir kullanıcı F1 tuşuna bastığında genel, ancak uygun bir Yardım konusunun tasarımcı ya da düzenleyici için görüntülenmesini sağlayacak şekilde yapılır. Bir düzenleyici, buna ek olarak imlecin geçerli anahtar sözcüğünü veya geçerli seçime bağlı olarak bir anahtar terimi vermenizi sağlamalıdır. Bu, Kullanıcı F1 tuşuna bastığında, veya seçilen metin veya UI öğesi için Yardım konusunun görüntülenmesini sağlamak için yapılır. Tasarımcı, bir tasarımcıda seçilen bir öğe için bir formdaki düğme gibi bağlam sağlar. Düzenleyiciler ve tasarımcılar, [eski dil hizmeti temel](../extensibility/internals/legacy-language-service-essentials.md)bileşenleri 'nde özetlenen bir dil hizmetine de bağlanmalıdır.
