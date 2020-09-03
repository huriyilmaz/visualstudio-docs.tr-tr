---
title: Kaynak denetimi VSPackage 'ı uygulayıp uygulamamaya karar verme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196795"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Kaynak Denetimi VSPackage’ının Uygulanıp Uygulanmayacağını Belirleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölüm, kaynak denetimi çözümlerini genişletmek için kaynak denetimi eklentilerinin ve kaynak denetimi VSPackages 'ın seçimlerini elaborates ve uygun bir tümleştirme yolu seçme hakkında geniş yönergeler sağlar.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Sınırlı kaynaklarla küçük kaynak denetimi çözümü  
 Sınırlı kaynaklarınız varsa ve kaynak denetim paketi yazma ek yüküne sahip değilseniz, kaynak denetimi eklentisi API tabanlı eklentiler oluşturabilirsiniz. Bu, kaynak denetimi paketleriyle yan yana çalışmanıza olanak sağlar ve isteğe bağlı olarak kaynak denetimi eklentileri ve paketleri arasında geçiş yapabilirsiniz. Daha fazla bilgi için bkz. [kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Zengin özellik kümesine sahip büyük kaynak denetimi çözümü  
 Kaynak denetimi eklentisi API 'SI kullanılarak yeterince yakalanmayan zengin kaynak denetimi modeli sağlayan bir kaynak denetimi çözümü uygulamak istiyorsanız, tümleştirme yolu olarak bir kaynak denetim paketi düşünebilirsiniz. Kaynak denetim olaylarını özel bir şekilde işleyebilmeniz için, bu durum özellikle kaynak denetim bağdaştırıcısı paketini (kaynak denetimi eklentileri ile iletişim kuran ve temel bir kaynak denetimi kullanıcı arabirimi sağlar) yerine yenilerini koymak istiyorsanız geçerlidir. Zaten tatmin edici bir kaynak denetimi kullanıcı arabirimine sahipseniz ve bu deneyimi ' de korumak istiyorsanız [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , kaynak denetimi paketi seçeneği yalnızca bunu yapmanızı sağlar. Kaynak denetim paketi genel değildir ve yalnızca IDE ile kullanılmak üzere tasarlanmıştır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Kaynak Denetim mantığı ve Kullanıcı arabirimi üzerinde esneklik ve daha zengin denetim sağlayan bir kaynak denetimi çözümü uygulamak istiyorsanız, kaynak denetimi paketi tümleştirme yolunu tercih edebilirsiniz. Seçenekleriniz şunlardır:  
  
1. Kendi kaynak denetimi VSPackage 'ı kaydedin (bkz. [kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Varsayılan kaynak denetimi kullanıcı arabirimini özel Kullanıcı arabiriminiz ile değiştirin (bkz. [Özel Kullanıcı arabirimi](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Kullanılacak glifleri belirtin ve Çözüm Gezgini glif olaylarını işleyin (bkz. [glif denetimi](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Sorgu düzenleme ve sorgu kaydetme olaylarını işle (bkz. sorgu [düzenleme sorgusu kaydetme](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi Oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
