---
title: Proje türü tasarım kararları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704078"
---
# <a name="project-type-design-decisions"></a>Proje Türü Tasarım Kararları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir proje türü oluşturmadan önce, proje türü ile ilgili çeşitli tasarım kararları almanız gerekir. Projelerinize hangi öğe türlerinin ekleneceğini, proje dosyalarının nasıl kalıcı olacağını ve hangi taahhüt modelinin kullanılacağını karar vermelisiniz.  
  
## <a name="project-items"></a>Proje öğeleri  
 Projeniz dosyaları veya soyut nesneleri kullanacak mı? Dosyaları kullanıyorsanız, bunlara başvuru tabanlı veya dizin tabanlı dosyalar olur. Dosyalar veya soyut nesneler yerel veya uzak olacak mı?  
  
 Projedeki öğeler dosyalar olabilir veya bir veritabanı deposundaki nesneler veya Internet üzerindeki veri bağlantıları gibi daha soyut nesneler olabilir. Öğeler dosyalar ise, proje başvuru tabanlı ya da dizin tabanlı bir proje olabilir.  
  
 Başvuru tabanlı projelerde, öğeler birden fazla projede görünebilir. Ancak, bir öğenin temsil ettiği gerçek dosya yalnızca bir dizinde bulunur. Dizin tabanlı projelerde, tüm proje öğeleri dizin yapısında bulunur. Daha fazla bilgi için bkz. [nib: projelerdeki öğe yönetimi](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Yerel öğeler, uygulamanın yüklü olduğu bilgisayarda depolanır. Uzak öğeler, yerel ağdaki ayrı bir sunucuda veya Internet 'te başka bir yerde depolanabilir.  
  
## <a name="project-file-persistence"></a>Proje dosyası kalıcılığı  
 Veriler ortak düz dosya sistemlerinde mi, yoksa yapılandırılmış depolamada mı depolanacak? Dosyalar standart bir düzenleyici veya projeye özgü bir düzenleyici kullanılarak açılacak mi?  
  
 Verilerini kalıcı hale getirmek için, çoğu uygulama verilerini bir dosyaya kaydeder ve bir kullanıcının bilgileri gözden geçirmesi veya değiştirmesi gerektiğinde onu geri okur.  
  
 Birleşik dosyalar olarak da adlandırılan yapılandırılmış depolama, genellikle birkaç bileşen nesne modeli (COM) nesnesinin kalıcı verilerini tek bir dosyada depolaması gerektiğinde kullanılır. Yapılandırılmış depolama ile, çeşitli farklı yazılım bileşenleri tek bir disk dosyasını paylaşabilir.  
  
 Projenizdeki öğelerin kalıcılığını göz önünde bulundurmanız gereken birkaç seçeneğiniz vardır. Aşağıdaki seçeneklerden herhangi birini yapabilirsiniz:  
  
- Her dosyayı değiştirildiğinde tek tek kaydedin.  
  
- Tek bir **kaydetme** işleminde çok sayıda işlem yakalayın.  
  
- Dosyaları yerel olarak kaydedin ve sonra bir sunucuya yayımlayın veya öğe, uzak bir nesne ile bir veri bağlantısını temsil ettiğinde proje öğelerini kaydetmek için başka bir yaklaşım kullanın.  
  
  Kalıcılık hakkında daha fazla bilgi için bkz. [Proje kalıcılığı](../../extensibility/internals/project-persistence.md) ve [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Proje taahhüt modeli  
 Kalıcı veri nesneleri doğrudan modda veya işlem temelli modda açılacak mı?  
  
 Veri nesneleri doğrudan modda açıldığında, verilerde yapılan değişiklikler anında veya Kullanıcı dosyayı el ile kaydettiğinde eklenir.  
  
 Veri nesneleri işlem temelli mod kullanılarak açıldığında, değişiklikler bellekteki geçici bir konuma kaydedilir ve Kullanıcı el ile dosyayı kaydetmeyi seçinceye kadar kaydedilmez. Bu sırada, tüm değişikliklerin birlikte gerçekleşmesi veya hiçbir değişiklik yapılmayacak olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: projelerdeki öğe yönetimi](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Proje kalıcılığı](../../extensibility/internals/project-persistence.md)   
 [Proje modelinin öğeleri](../../extensibility/internals/elements-of-a-project-model.md)   
 [Proje modeli çekirdek bileşenleri](../../extensibility/internals/project-model-core-components.md)   
 [Proje Türleri Oluşturma](../../extensibility/internals/creating-project-types.md)
