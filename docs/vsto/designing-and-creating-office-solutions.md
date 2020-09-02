---
title: Office çözümleri tasarlama ve oluşturma
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 385d313d0a8796d2aba93903e95e989ac1e0ced6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189718"
---
# <a name="design-and-create-office-solutions"></a>Office çözümleri tasarlama ve oluşturma

Visual Studio, birçok farklı Office çözümü türü oluşturmak için kullanabileceğiniz proje şablonları sağlar. Belgelerinin bu bölümü proje şablonlarını açıklar ve Office projeleri oluşturma hakkında rehberlik sağlar. Projenizi oluşturduktan sonra kod ve Kullanıcı arabirimi özelleştirmelerini uygulama hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirme](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Office projeleri oluşturma
 Başlamadan önce, gereksinimlerinizi saptamalı ve en iyi sığacak çözüm türünü bulmalısınız. Örneğin, Office çözümünüzün uygulama her kullanıldığında çalışması gerekiyorsa, bir VSTO eklentisi gereksinimlerinize en uygun şekilde uyar. Kod tek bir belgeyle sıkı bir şekilde tümleştirildiğinde, belge düzeyinde bir özelleştirme oluşturun. Bu proje türleri, Visual Studio proje şablonları olarak kullanılabilir. Visual Studio 'da yer alan Office proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md). Office projelerinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Office projelerinin, Visual Studio 'daki diğer proje türlerinden farklı özellikleri ve proje öğeleri vardır. Örneğin, belge düzeyinde bir proje oluşturduğunuzda, projenizdeki belge veya çalışma kitabı Visual Studio içinde açılabilir ve düzenlenebilir. Daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>.NET Framework sürümü seçin
 Gereksinimlerinize en uygun proje türünü seçtikten sonra, geliştirme sürecinizdeki hangi .NET Framework sürümünü kullanacağınızı seçebilirsiniz. Office projelerinde aşağıdaki .NET Framework sürümlerini hedefleyebilirsiniz:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  Projeniz için seçtiğiniz .NET Framework sürümü, çözümünüzün çalışması için son kullanıcı bilgisayarlarında gereklidir. Örneğin, projeniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ' i hedefliyorsa, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında gereklidir. Bu örnekte, son kullanıcı bilgisayarlarında yalnızca .NET Framework 3,5 yüklüyse çözümünüz çalışmaz.

  .NET Framework 3,5 ' i hedefleyen bir VSTO eklenti projesini geçirirseniz, Visual Studio, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklediğiniz Office sürümüne bağlı olarak projenizin hedef çerçevesini veya daha yenisini değiştirir.

  Ancak, Visual Studio hedef Framework 'ü değiştirdikten sonra, belirli özellikleri kullanıyorsa projenizdeki bazı kodları değiştirmeniz gerekebilir. Hedef Framework 'ün nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md). Projenizde yapmanız gerekebilecek değişiklikler hakkında daha fazla bilgi için bkz. [Office çözümlerini .NET Framework 4 veya sonraki bir sürüme geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

  Visual Studio, projeniz için hedef .NET Framework değiştirirse ve çözümünüzü dağıtmak için ClickOnce kullanıyorsanız, **Önkoşullar** iletişim kutusunda .NET Framework ilgili sürümü seçtiğinizden emin olun. Projeniz için hedef çerçeveyi değiştirdiğinizde bu seçim otomatik olarak değişmez. Daha fazla bilgi için bkz. [nasıl yapılır: Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yüklemek](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

> [!NOTE]
> Kullanarak oluşturduğunuz Office projelerinde .NET Framework 3,5 veya önceki bir sürümü hedeflenemez [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] . Kullanarak oluşturduğunuz Office projeleri [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , ilk olarak [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>Son kullanıcı bilgisayarlarında Office PIA 'ların ne zaman gerekli olduğunu anlayın
 Varsayılan olarak, projedeki her bir Office PIA başvurusunun **birlikte çalışma türlerini katıştır** özelliği **true**olarak ayarlandıysa ve varsayılan değer olan Office birincil birlikte çalışma derlemelerinin (PIA 'lar) Son Kullanıcı bilgisayarlara yüklenmesi gerekmez. Bu senaryoda, çözümünüz tarafından kullanılan PIA türleri için tür bilgileri, projeyi oluştururken çözüm derlemesine katıştırılır. Çalışma zamanında, Office uygulamasının COM tabanlı nesne modeline çağrı yapmak için PIA yerine gömülü tür bilgileri kullanılır. PIA 'lerden gelen türlerin çözümünüze nasıl katıştırıldığı hakkında daha fazla bilgi için bkz. [tür denklik ve katıştırılmış birlikte çalışma türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 Projedeki her bir Office PIA başvurusunun **birlikte çalışma türlerini katıştır** özelliği **yanlış**olarak ayarlanırsa, Office PIA 'ları çözümü çalıştıran her bir son kullanıcı bilgisayarında genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. Çoğu durumda, PIA 'ler Office ile varsayılan olarak yüklenir, ancak aynı zamanda sizin çözümünüz için bir önkoşul olarak PIA Redistributable da dahil edebilirsiniz. Daha fazla bilgi için bkz. [dağıtım Için Office çözüm önkoşulları](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).

### <a name="understand-the-client-profile"></a>İstemci profilini anlayın
 .NET Framework Istemci profili, tam .NET Framework bir alt kümesidir. Yalnızca .NET Framework istemci özelliklerini kullanmanız gerekiyorsa ve Office çözümünüz için mümkün olan en hızlı dağıtım deneyimini sağlamak istiyorsanız .NET Framework Istemci profilini hedefleyebilirsiniz. Daha fazla bilgi için bkz. [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).

 ' İ hedefleyen bir Office projesi oluşturduğunuzda, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] Varsayılan olarak hedeflenmelidir. Tam için geliştirme yapmak istiyorsanız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bu seçeneği Proje oluşturulduktan sonra ayarlamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Microsoft Office 64 bit sürümü için çözümler oluşturma
 Microsoft Office, 64-bit ve 32 bit sürümlerde kullanılabilir. Her iki sürümde çalışabilen Office çözümleri oluşturmak için, projenizin platform hedefi ayarı **herhangi BIR CPU**olarak ayarlanmalıdır. Bu, Office projeleri için varsayılan değerdir. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Microsoft Office 'ın 64-bit ve 32 bit sürümleri tarafından kullanılan ayrı 64-bit ve 32 bit sürümleri vardır. Daha fazla bilgi için bkz. [Office çalışma zamanına genel bakış Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Office çözümlerinde derlemeler
 Visual Studio 'da Office geliştirme araçları 'nı kullanarak bir Office projesi oluşturduğunuzda, yazdığınız kod sonunda bir derlemeye derlenir. Derleme paylaşılan bir sunucuya veya istemci bilgisayardaki bir dizine dağıtılır.

 Office çözümlerinde derlemeler bir Office uygulaması tarafından yüklenir. Derleme yüklendikten sonra, derlemedeki kod uygulamada oluşturulan olaylara yanıt verebilir, örneğin, bir Kullanıcı bir menü öğesini tıkladığında. Derlemedeki kod ayrıca, uygulamayı otomatikleştirebilmek ve genişletmek için nesne modelini çağırabilir ve içindeki sınıflardan herhangi birini kullanabilir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] . Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md) ve [VSTO eklentilerinin mimarisi](../vsto/architecture-of-vsto-add-ins.md).

 Office çözümleri derlemeyi tanımlamak için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Bildirimler derlemenin adı, sürümü ve konumu hakkında bilgiler içerir, böylece uygulamanın doğru derlemeyi bulabileceği, bağlayabilmesi ve çalıştırmasına olanak sağlar. Daha fazla bilgi için bkz. [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Belge düzeyi projeleri bir derlemeye ek olarak bir belge içerir. Belge, uygulamanın ön ucu olarak davranır ve tüm kullanıcı etkileşiminin gerçekleştiği yerdir. Her belgeye ilişkili yalnızca bir tane ana proje derlemesi olabilir; Ancak, birden çok belge aynı derlemeye işaret edebilir.

 Belge düzeyi projelerdeki derlemeler belgeye katıştırılmıyor; Bunun yerine, başka bir yerde depolanır ve belgenin uygulama bildirimi tarafından tanımlanır.

## <a name="security-considerations-for-assemblies"></a>Derlemeler için güvenlik konuları
 Bir Office çözümünün bir bilgisayarda çalışması için, çözüm tarafından kullanılan derlemelerin çalışması için güvenilir olması gerekir. Güvenlik hakkında daha fazla bilgi için bkz. [Secure Office Solutions](../vsto/securing-office-solutions.md).

 Varsayılan olarak, çözüm derlemesi ve projenizin çıkış klasöründeki tüm başvurulan derlemeler, projeyi oluşturduğunuzda geliştirme bilgisayarında çalışmak üzere güvenilirdir. Daha fazla bilgi için bkz. [Office çözümleri oluşturma](../vsto/building-office-solutions.md).

 Güvenlik nedenleriyle, paylaşılan bir konumda geliştirme yerine, yerel bilgisayarınızda proje oluşturmak en iyisidir. Daha fazla bilgi için bkz. [Office çözümlerini Işbirliğine dayalı geliştirme](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Başvurulan derlemeler
 Derleme, Proje başvurularında listelenen diğer derlemelere başvurabilir. Ancak, bir belge düzeyindeki proje derlemesi başka bir belge düzeyi proje derlemesine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Office projelerindeki Özellikler](../vsto/properties-in-office-projects.md)
- [Farklı Microsoft Office sürümlerinde çözüm çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [Nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Nasıl yapılır: bir Office çözümü için yapılandırma bilgilerini ayarlama](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Visual Studio içinde Office işlevselliğini kullanma](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Visual Studio 'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
