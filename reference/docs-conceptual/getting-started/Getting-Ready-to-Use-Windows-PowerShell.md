---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Vorbereiten des Verwendens von WindowsPowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: a87ec614a45f0b6c05c530110e52f87c646b3e8b
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="getting-ready-to-use-windows-powershell"></a><span data-ttu-id="1e54f-103">Vorbereiten des Verwendens von WindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="1e54f-103">Getting Ready to Use Windows PowerShell</span></span>
<span data-ttu-id="1e54f-104">Wenn Sie die Windows PowerShell installieren und ausführen, sollten Sie die folgenden Setupoptionen berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="1e54f-104">When Windows PowerShell is installed and started, consider the following setup options.</span></span> <span data-ttu-id="1e54f-105">Sie können diese Aufgaben zu einem beliebigen Zeitpunkt ausführen.</span><span class="sxs-lookup"><span data-stu-id="1e54f-105">You can perform these tasks at any time.</span></span>

- <span data-ttu-id="1e54f-106">**Installieren von Hilfedateien.**</span><span class="sxs-lookup"><span data-stu-id="1e54f-106">**Install help files.**</span></span> <span data-ttu-id="1e54f-107">Die Cmdlets, die in Windows PowerShell 3.0 enthalten sind, werden zunächst ohne Hilfedateien bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="1e54f-107">The cmdlets that are included in Windows PowerShell 3.0 do not come with help files.</span></span> <span data-ttu-id="1e54f-108">Sie können aber das Cmdlet [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) verwenden, um die neuesten Hilfedateien auf Ihren Computer herunterzuladen und zu installieren.</span><span class="sxs-lookup"><span data-stu-id="1e54f-108">However, you can use the [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet to download and install the newest help files on your computer.</span></span> <span data-ttu-id="1e54f-109">Wenn diese Dateien installiert sind, können Sie das Cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) verwenden, um sie direkt über die Befehlszeile anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1e54f-109">When the files are installed, you can use the [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet to display them right at the command line.</span></span> <span data-ttu-id="1e54f-110">Weitere Informationen hierzu finden Sie unter [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).</span><span class="sxs-lookup"><span data-stu-id="1e54f-110">For more information, see [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).</span></span>

    <span data-ttu-id="1e54f-111">Wenn Sie sich entscheiden, die Hilfedateien nicht zu installieren, können Sie die Hilfethemen weiterhin online lesen.</span><span class="sxs-lookup"><span data-stu-id="1e54f-111">If you decide not to install the help files, you can still read the help topics online.</span></span> <span data-ttu-id="1e54f-112">Um die Onlineversion eines Cmdlet-Hilfethemas zu finden, geben Sie `Get-Help <CmdletName> -Online` ein.</span><span class="sxs-lookup"><span data-stu-id="1e54f-112">To find the online version of any cmdlet help topic, type: `Get-Help <CmdletName> -Online`.</span></span> <span data-ttu-id="1e54f-113">Wenn Sie die Windows PowerShell-Hilfethemen in der TechNet-Bibliothek durchsuchen möchten, beginnen Sie bei [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116).</span><span class="sxs-lookup"><span data-stu-id="1e54f-113">To browse the Windows PowerShell help topics in the TechNet Library, start at [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116).</span></span>

- <span data-ttu-id="1e54f-114">**Ausführen von Skripts.**</span><span class="sxs-lookup"><span data-stu-id="1e54f-114">**Run scripts.**</span></span> <span data-ttu-id="1e54f-115">Um die Sicherheit von Windows PowerShell zu gewährleisten, ist die Standardausführungsrichtlinie in Windows PowerShell **Eingeschränkt**.</span><span class="sxs-lookup"><span data-stu-id="1e54f-115">To keep Windows PowerShell secure, the default execution policy on Windows PowerShell is **Restricted**.</span></span> <span data-ttu-id="1e54f-116">Diese Richtlinie lässt das Ausführen von Cmdlets, aber nicht das Ausführen von Skripts zu.</span><span class="sxs-lookup"><span data-stu-id="1e54f-116">This policy allows you to run cmdlets, but not scripts.</span></span> <span data-ttu-id="1e54f-117">Wenn Sie Skripts ausführen möchten, verwenden Sie das Cmdlet [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab), um die Ausführungsrichtlinie in **AllSigned** oder **RemoteSigned** zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1e54f-117">To run scripts, use the [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) cmdlet to change the execution policy to **AllSigned** or **RemoteSigned**.</span></span> <span data-ttu-id="1e54f-118">Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1e54f-118">Only members of the Administrators group on the computer can run this cmdlet.</span></span> <span data-ttu-id="1e54f-119">Weitere Informationen hierzu finden Sie unter [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).</span><span class="sxs-lookup"><span data-stu-id="1e54f-119">For more information, see [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).</span></span>

- <span data-ttu-id="1e54f-120">**Aktivieren von Remoting.**</span><span class="sxs-lookup"><span data-stu-id="1e54f-120">**Enable remoting.**</span></span> <span data-ttu-id="1e54f-121">Das System ist bereits so konfiguriert, dass es Remotebefehle auf anderen Computern ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="1e54f-121">The system is already configured for you to run remote commands on other computers.</span></span> <span data-ttu-id="1e54f-122">Unter Windows Server 2012 R2 und Windows Server 2012 ist das System ebenfalls für das Empfangen von Remotebefehlen konfiguriert, d.h. es gestattet anderen Computern, Remotebefehle auf dem lokalen Computer auszuführen.</span><span class="sxs-lookup"><span data-stu-id="1e54f-122">On Windows Server 2012 R2 and Windows Server 2012, the system is also configured to receive remote commands, that is, to allow other computers to run remote commands on the local computer.</span></span> <span data-ttu-id="1e54f-123">Wenn Sie für einen Computer, auf dem eine andere Version von Windows ausgeführt wird, das Empfangen von Remotebefehlen ermöglichen möchten, führen Sie das Cmdlet [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) auf diesem Computer aus.</span><span class="sxs-lookup"><span data-stu-id="1e54f-123">To enable computers running other versions of Windows to receive remote commands, run the [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) cmdlet on the computer that you want to manage remotely.</span></span> <span data-ttu-id="1e54f-124">Dieses Cmdlet kann nur von Mitgliedern der Gruppe „Administratoren“ auf dem Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1e54f-124">Only members of the Administrators group on the computer can run this cmdlet.</span></span> <span data-ttu-id="1e54f-125">Weitere Informationen hierzu finden Sie unter [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970).</span><span class="sxs-lookup"><span data-stu-id="1e54f-125">For more information, see [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970).</span></span>

    <span data-ttu-id="1e54f-126">HINWEIS: Ist Remoting auf einem Computer unter Windows PowerShell 2.0 aktiviert, ist es auch nach der Installation von Windows Management Framework 3.0 weiterhin aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1e54f-126">NOTE: If remoting is enabled on a computer that is running Windows PowerShell 2.0, remoting is still enabled after you install Windows Management Framework 3.0.</span></span> <span data-ttu-id="1e54f-127">Allerdings müssen Sie Remoting unter Windows Server 2008 (nicht Windows Server 2008 R2) nach der Installation von Windows Management Framework 3.0 erneut aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1e54f-127">However, on Windows Server 2008 (not Windows Server 2008 R2), you must re-enable remoting after installing Windows Management Framework 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e54f-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1e54f-128">See Also</span></span>
- [<span data-ttu-id="1e54f-129">Installieren von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e54f-129">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)
- <span data-ttu-id="1e54f-130">[Starten von Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)</span><span class="sxs-lookup"><span data-stu-id="1e54f-130">[Starting Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)</span></span>
