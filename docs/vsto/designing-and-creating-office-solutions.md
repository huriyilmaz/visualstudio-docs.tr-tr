---
title: Office çözümleri tasarlama ve oluşturma
description: Visual Studio, farklı türlerde Office çözümleri oluşturmak için kullanabileceğiniz proje şablonlarını nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 248fe0caba9d1fbfca34c49b63ccf7bea31ea3de
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038090"
---
# <a name="design-and-create-office-solutions"></a>Office çözümleri tasarlama ve oluşturma

Visual Studio, birkaç farklı türde Office çözüm oluşturmak için kullanabileceğiniz proje şablonları sağlar. belgelerinin bu bölümü proje şablonlarını açıklar ve Office projeleri oluşturma hakkında rehberlik sağlar. projenizi oluşturduktan sonra kod ve kullanıcı arabirimi özelleştirmelerini uygulama hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirme](../vsto/developing-office-solutions.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-office-projects"></a>Office projeleri oluşturma
 Başlamadan önce, gereksinimlerinizi saptamalı ve en iyi sığacak çözüm türünü bulmalısınız. örneğin, Office çözümünüzün uygulama her kullanıldığında çalışması gerekiyorsa, gereksinimlerinize en uygun bir VSTO eklenti vardır. Kod tek bir belgeyle sıkı bir şekilde tümleştirildiğinde, belge düzeyinde bir özelleştirme oluşturun. bu proje türleri Visual Studio proje şablonları olarak kullanılabilir. Visual Studio eklenen Office proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md). Office projelerinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projeleri oluşturma Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Office projelerde, Visual Studio diğer proje türlerinden farklı özellik ve proje öğeleri bulunur. Örneğin, belge düzeyinde bir proje oluşturduğunuzda, projenizdeki belge veya çalışma kitabı Visual Studio içinde açılabilir ve düzenlenebilir. daha fazla bilgi için bkz. [Visual Studio ortamındaki Office projeler](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="choose-a-net-framework-version"></a>.NET Framework sürümü seçin
 gereksinimlerinize en uygun proje türünü seçtikten sonra, geliştirme sürecinizdeki hangi .NET Framework sürümünü kullanacağınızı seçebilirsiniz. aşağıdaki .NET Framework sürümlerini Office projelerinde hedefleyebilirsiniz:

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]

- [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

- [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]

  projeniz için seçtiğiniz .NET Framework sürümü, çözümünüzün çalışması için son kullanıcı bilgisayarlarında gereklidir. Örneğin, projeniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ' i hedefliyorsa, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] son kullanıcı bilgisayarlarında gereklidir. bu örnekte, son kullanıcı bilgisayarlarında yalnızca .NET Framework 3,5 yüklüyse çözümünüz çalışmaz.

  .NET Framework 3,5 ' i hedefleyen VSTO bir eklenti projesini geçirirseniz Visual Studio, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] yüklemiş olduğunuz Office sürümüne bağlı olarak projenizin hedef çerçevesini veya daha sonra değiştirir.

  ancak, Visual Studio hedef framework 'ü değiştirdikten sonra, projenizdeki bazı kodları belirli özellikleri kullanıyorsa değiştirmeniz gerekebilir. Hedef Framework 'ün nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md). projenizde yapmanız gerekebilecek değişiklikler hakkında daha fazla bilgi için, [.NET Framework 4 veya sonraki bir sürüme Office çözümleri geçirme](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)konusuna bakın.

  Visual Studio, projeniz için hedef .NET Framework değiştirirse ve çözümünüzü dağıtmak için ClickOnce kullanıyorsanız, **önkoşullar** iletişim kutusunda .NET Framework karşılık gelen sürümünü de seçtiğinizden emin olun. Projeniz için hedef çerçeveyi değiştirdiğinizde bu seçim otomatik olarak değişmez. daha fazla bilgi için bkz. [nasıl yapılır: son kullanıcı bilgisayarlarına önkoşulları yüklemek Office çözümleri çalıştırmak için](/previous-versions/bb608608(v=vs.110)).

> [!NOTE]
> kullanarak oluşturduğunuz Office projelerinde .NET Framework 3,5 veya önceki bir sürümü hedeflenemez [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] . kullanarak oluşturduğunuz Office projeleri [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , ilk olarak[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]

### <a name="understand-when-the-office-pias-are-required-on-end-user-computers"></a>son kullanıcı bilgisayarlarında Office pıa 'ların ne zaman gerekli olduğunu anlayın
 varsayılan olarak, Office birincil birlikte çalışma derlemeleri (pıa 'lar), projedeki her bir Office pıa başvurusunun **birlikte çalışma türlerini katıştır** özelliği **True** olarak ayarlanırsa, bu varsayılan değer olan son kullanıcı bilgisayarlarına yüklenmelidir. Bu senaryoda, çözümünüz tarafından kullanılan PIA türleri için tür bilgileri, projeyi oluştururken çözüm derlemesine katıştırılır. çalışma zamanında, Office uygulamasının COM tabanlı nesne modeline çağırmak için pıa yerine gömülü tür bilgileri kullanılır. PIA 'lerden gelen türlerin çözümünüze nasıl katıştırıldığı hakkında daha fazla bilgi için bkz. [tür denklik ve katıştırılmış birlikte çalışma türleri](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).

 projedeki her bir Office pıa başvurusunun **birlikte çalışma türlerini katıştır** özelliği **False** olarak ayarlanırsa, Office pıa 'ler çözümü çalıştıran her bir son kullanıcı bilgisayarında genel derleme önbelleğinde yüklü ve kayıtlı olmalıdır. çoğu durumda, pıa 'ler Office varsayılan olarak yüklenir, ancak sizin çözümünüz için bir önkoşul olarak pıa redistributable da dahil edebilirsiniz. daha fazla bilgi için bkz. [dağıtım için Office çözüm önkoşulları](/previous-versions/bb608617(v=vs.110)).

### <a name="understand-the-client-profile"></a>İstemci profilini anlayın
 .NET Framework istemci profili, tam .NET Framework bir alt kümesidir. yalnızca .NET Framework istemci özelliklerini kullanmanız gerekiyorsa ve Office çözümünüz için mümkün olan en hızlı dağıtım deneyimini sağlamak istiyorsanız .NET Framework istemci profilini hedefleyebilirsiniz. daha fazla bilgi için bkz. [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile).

 öğesini hedefleyen bir Office projesi oluşturduğunuzda, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] varsayılan olarak hedeflenmelidir. Tam için geliştirme yapmak istiyorsanız [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , bu seçeneği Proje oluşturulduktan sonra ayarlamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

## <a name="create-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Microsoft Office 64 bit sürümü için çözümler oluşturma
 Microsoft Office, 64-bit ve 32 bit sürümlerde kullanılabilir. her iki sürümde çalışabilen Office çözümler oluşturmak için, projenizin platform hedefi ayarı **herhangi bir CPU** olarak ayarlanmalıdır. bu, Office projeleri için varsayılan değerdir. daha fazla bilgi için bkz. [derleme Office çözümleri](../vsto/building-office-solutions.md).

 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Microsoft Office 'ın 64-bit ve 32 bit sürümleri tarafından kullanılan ayrı 64-bit ve 32 bit sürümleri vardır. daha fazla bilgi için bkz. [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-office-solutions"></a>Office çözümlerinde derlemeler
 Visual Studio Office geliştirme araçlarını kullanarak bir Office projesi oluşturduğunuzda yazdığınız kod sonunda bir derlemeye derlenir. Derleme paylaşılan bir sunucuya veya istemci bilgisayardaki bir dizine dağıtılır.

 Office çözümlerinde derlemeler Office bir uygulama tarafından yüklenir. Derleme yüklendikten sonra, derlemedeki kod uygulamada oluşturulan olaylara yanıt verebilir, örneğin, bir Kullanıcı bir menü öğesini tıkladığında. Derlemedeki kod ayrıca, uygulamayı otomatikleştirebilmek ve genişletmek için nesne modelini çağırabilir ve içindeki sınıflardan herhangi birini kullanabilir [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] . daha fazla bilgi için bkz. [belge düzeyi özelleştirmeleri](../vsto/architecture-of-document-level-customizations.md) ve [VSTO eklentilerin mimarisi](../vsto/architecture-of-vsto-add-ins.md)mimarisi.

 Office çözümler, derlemeyi tanımlamak için dağıtım bildirimlerini ve uygulama bildirimlerini kullanır. Bildirimler derlemenin adı, sürümü ve konumu hakkında bilgiler içerir, böylece uygulamanın doğru derlemeyi bulabileceği, bağlayabilmesi ve çalıştırmasına olanak sağlar. daha fazla bilgi için [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)bölümüne bakın.

 Belge düzeyi projeleri bir derlemeye ek olarak bir belge içerir. Belge, uygulamanın ön ucu olarak davranır ve tüm kullanıcı etkileşiminin gerçekleştiği yerdir. Her belgeye ilişkili yalnızca bir tane ana proje derlemesi olabilir; Ancak, birden çok belge aynı derlemeye işaret edebilir.

 Belge düzeyi projelerdeki derlemeler belgeye katıştırılmıyor; Bunun yerine, başka bir yerde depolanır ve belgenin uygulama bildirimi tarafından tanımlanır.

## <a name="security-considerations-for-assemblies"></a>Derlemeler için güvenlik konuları
 bir Office çözümünün bir bilgisayarda çalışması için, çözüm tarafından kullanılan derlemelerin çalışması için güvenilir olması gerekir. güvenlik hakkında daha fazla bilgi için bkz. [Secure Office solutions](../vsto/securing-office-solutions.md).

 Varsayılan olarak, çözüm derlemesi ve projenizin çıkış klasöründeki tüm başvurulan derlemeler, projeyi oluşturduğunuzda geliştirme bilgisayarında çalışmak üzere güvenilirdir. daha fazla bilgi için bkz. [derleme Office çözümleri](../vsto/building-office-solutions.md).

 Güvenlik nedenleriyle, paylaşılan bir konumda geliştirme yerine, yerel bilgisayarınızda proje oluşturmak en iyisidir. daha fazla bilgi için bkz. [Office çözümlerin işbirliğine dayalı geliştirmesi](../vsto/collaborative-development-of-office-solutions.md).

## <a name="referenced-assemblies"></a>Başvurulan derlemeler
 Derleme, Proje başvurularında listelenen diğer derlemelere başvurabilir. Ancak, bir belge düzeyindeki proje derlemesi başka bir belge düzeyi proje derlemesine başvuramaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio ortamındaki projeleri Office](../vsto/office-projects-in-the-visual-studio-environment.md)
- [Office projelerindeki özellikler](../vsto/properties-in-office-projects.md)
- [Farklı Microsoft Office sürümlerinde çözüm çalıştırma](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
- [nasıl yapılır: birincil birlikte çalışma bütünleştirilmiş kodları aracılığıyla Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [nasıl yapılır: Office çözümü için yapılandırma bilgilerini ayarlama](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)
- [Visual Studio içinde Office işlevselliği kullanın](../vsto/using-office-functionality-inside-of-visual-studio.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Visual Studio Office çözümlerin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)