ForgeAI — Full Project Source Backup



> Generated backup of all source files.



\---



\## Table of Contents



1\. \[index.html](#indexhtml)

2\. \[index.css](#indexcss)

3\. \[tailwind.config.js](#tailwindconfigjs)

4\. \[App.jsx](#appjsx)

5\. \[pages/Builder.jsx](#pagesbuilderJsx)

6\. \[components/builder/FileExplorer.jsx](#componentsbuilderfileexplorerjsx)

7\. \[components/builder/CodeEditor.jsx](#componentsbuildercodeeditorjsx)

8\. \[components/builder/LivePreview.jsx](#componentsbuilderlivepreviewjsx)

9\. \[components/builder/AIChat.jsx](#componentsbuilderaichatjsx)

10\. \[components/builder/Terminal.jsx](#componentsbuilderterminalJsx)

11\. \[hooks/useBuilder.js](#hooksusebuilderjs)

12\. \[hooks/useProjectState.js](#hooksuseprojectstatejs)

13\. \[hooks/useCloudSync.js](#hooksuseCloudSyncjs)

14\. \[hooks/useLivePreview.js](#hooksuseLivePreviewjs)

15\. \[hooks/useAIGeneration.js](#hooksuseAIGenerationjs)

16\. \[hooks/useErrorTracker.js](#hooksuseErrorTrackerjs)

17\. \[lib/babelCompiler.js](#libbabelCompilerjs)

18\. \[lib/aiPipeline.js](#libaiPipelinejs)

19\. \[lib/constants.js](#libconstantsjs)

20\. \[lib/fileUtils.js](#libfileUtilsjs)

21\. \[lib/localCache.js](#liblocalCachejs)

22\. \[lib/previewSandbox.js](#libpreviewSandboxjs)



\---



\## index.html



```html

<!doctype html>

<html lang="en">

\&#x20; <head>

\&#x20;   <meta charset="UTF-8" />

\&#x20;   <link rel="icon" type="image/svg+xml" href="https://base44.com/logo\\\_v2.svg" />

\&#x20;   <meta name="viewport" content="width=device-width, initial-scale=1.0" />

\&#x20;   <link rel="manifest" href="/manifest.json" />

\&#x20;   <title>Base44 APP</title>

\&#x20; </head>

\&#x20; <body>

\&#x20;   <div id="root"></div>

\&#x20;   <script type="module" src="/src/main.jsx"></script>

\&#x20; </body>

</html>

```



\---



\## index.css



```css

@tailwind base;

@tailwind components;

@tailwind utilities;



@layer base {

\&#x20; :root {

\&#x20;   --background: 0 0% 100%;

\&#x20;   --foreground: 0 0% 3.9%;

\&#x20;   --card: 0 0% 100%;

\&#x20;   --card-foreground: 0 0% 3.9%;

\&#x20;   --popover: 0 0% 100%;

\&#x20;   --popover-foreground: 0 0% 3.9%;

\&#x20;   --primary: 0 0% 9%;

\&#x20;   --primary-foreground: 0 0% 98%;

\&#x20;   --secondary: 0 0% 96.1%;

\&#x20;   --secondary-foreground: 0 0% 9%;

\&#x20;   --muted: 0 0% 96.1%;

\&#x20;   --muted-foreground: 0 0% 45.1%;

\&#x20;   --accent: 0 0% 96.1%;

\&#x20;   --accent-foreground: 0 0% 9%;

\&#x20;   --destructive: 0 84.2% 60.2%;

\&#x20;   --destructive-foreground: 0 0% 98%;

\&#x20;   --border: 0 0% 89.8%;

\&#x20;   --input: 0 0% 89.8%;

\&#x20;   --ring: 0 0% 3.9%;

\&#x20;   --chart-1: 12 76% 61%;

\&#x20;   --chart-2: 173 58% 39%;

\&#x20;   --chart-3: 197 37% 24%;

\&#x20;   --chart-4: 43 74% 66%;

\&#x20;   --chart-5: 27 87% 67%;

\&#x20;   --radius: 0.5rem;

\&#x20;   --sidebar-background: 0 0% 98%;

\&#x20;   --sidebar-foreground: 240 5.3% 26.1%;

\&#x20;   --sidebar-primary: 240 5.9% 10%;

\&#x20;   --sidebar-primary-foreground: 0 0% 98%;

\&#x20;   --sidebar-accent: 240 4.8% 95.9%;

\&#x20;   --sidebar-accent-foreground: 240 5.9% 10%;

\&#x20;   --sidebar-border: 220 13% 91%;

\&#x20;   --sidebar-ring: 217.2 91.2% 59.8%;

\&#x20; }



\&#x20; .dark {

\&#x20;   --background: 0 0% 3.9%;

\&#x20;   --foreground: 0 0% 98%;

\&#x20;   --card: 0 0% 3.9%;

\&#x20;   --card-foreground: 0 0% 98%;

\&#x20;   --popover: 0 0% 3.9%;

\&#x20;   --popover-foreground: 0 0% 98%;

\&#x20;   --primary: 0 0% 98%;

\&#x20;   --primary-foreground: 0 0% 9%;

\&#x20;   --secondary: 0 0% 14.9%;

\&#x20;   --secondary-foreground: 0 0% 98%;

\&#x20;   --muted: 0 0% 14.9%;

\&#x20;   --muted-foreground: 0 0% 63.9%;

\&#x20;   --accent: 0 0% 14.9%;

\&#x20;   --accent-foreground: 0 0% 98%;

\&#x20;   --destructive: 0 62.8% 30.6%;

\&#x20;   --destructive-foreground: 0 0% 98%;

\&#x20;   --border: 0 0% 14.9%;

\&#x20;   --input: 0 0% 14.9%;

\&#x20;   --ring: 0 0% 83.1%;

\&#x20;   --chart-1: 220 70% 50%;

\&#x20;   --chart-2: 160 60% 45%;

\&#x20;   --chart-3: 30 80% 55%;

\&#x20;   --chart-4: 280 65% 60%;

\&#x20;   --chart-5: 340 75% 55%;

\&#x20;   --sidebar-background: 240 5.9% 10%;

\&#x20;   --sidebar-foreground: 240 4.8% 95.9%;

\&#x20;   --sidebar-primary: 224.3 76.3% 48%;

\&#x20;   --sidebar-primary-foreground: 0 0% 100%;

\&#x20;   --sidebar-accent: 240 3.7% 15.9%;

\&#x20;   --sidebar-accent-foreground: 240 4.8% 95.9%;

\&#x20;   --sidebar-border: 240 3.7% 15.9%;

\&#x20;   --sidebar-ring: 217.2 91.2% 59.8%;

\&#x20; }

}



@layer base {

\&#x20; \\\* {

\&#x20;   @apply border-border outline-ring/50;

\&#x20; }



\&#x20; body {

\&#x20;   @apply bg-background text-foreground;

\&#x20; }

}

```



\---



\## tailwind.config.js



```js

/\\\*\\\* @type {import('tailwindcss').Config} \\\*/

module.exports = {

\&#x20;   darkMode: \\\["class"],

\&#x20;   content: \\\["./index.html", "./src/\\\*\\\*/\\\*.{ts,tsx,js,jsx}"],

\&#x20; theme: {

\&#x20; 	extend: {

\&#x20; 		borderRadius: {

\&#x20; 			lg: 'var(--radius)',

\&#x20; 			md: 'calc(var(--radius) - 2px)',

\&#x20; 			sm: 'calc(var(--radius) - 4px)'

\&#x20; 		},

\&#x20; 		colors: {

\&#x20; 			background: 'hsl(var(--background))',

\&#x20; 			foreground: 'hsl(var(--foreground))',

\&#x20; 			card: {

\&#x20; 				DEFAULT: 'hsl(var(--card))',

\&#x20; 				foreground: 'hsl(var(--card-foreground))'

\&#x20; 			},

\&#x20; 			popover: {

\&#x20; 				DEFAULT: 'hsl(var(--popover))',

\&#x20; 				foreground: 'hsl(var(--popover-foreground))'

\&#x20; 			},

\&#x20; 			primary: {

\&#x20; 				DEFAULT: 'hsl(var(--primary))',

\&#x20; 				foreground: 'hsl(var(--primary-foreground))'

\&#x20; 			},

\&#x20; 			secondary: {

\&#x20; 				DEFAULT: 'hsl(var(--secondary))',

\&#x20; 				foreground: 'hsl(var(--secondary-foreground))'

\&#x20; 			},

\&#x20; 			muted: {

\&#x20; 				DEFAULT: 'hsl(var(--muted))',

\&#x20; 				foreground: 'hsl(var(--muted-foreground))'

\&#x20; 			},

\&#x20; 			accent: {

\&#x20; 				DEFAULT: 'hsl(var(--accent))',

\&#x20; 				foreground: 'hsl(var(--accent-foreground))'

\&#x20; 			},

\&#x20; 			destructive: {

\&#x20; 				DEFAULT: 'hsl(var(--destructive))',

\&#x20; 				foreground: 'hsl(var(--destructive-foreground))'

\&#x20; 			},

\&#x20; 			border: 'hsl(var(--border))',

\&#x20; 			input: 'hsl(var(--input))',

\&#x20; 			ring: 'hsl(var(--ring))',

\&#x20; 			chart: {

\&#x20; 				'1': 'hsl(var(--chart-1))',

\&#x20; 				'2': 'hsl(var(--chart-2))',

\&#x20; 				'3': 'hsl(var(--chart-3))',

\&#x20; 				'4': 'hsl(var(--chart-4))',

\&#x20; 				'5': 'hsl(var(--chart-5))'

\&#x20; 			},

\&#x20; 			sidebar: {

\&#x20; 				DEFAULT: 'hsl(var(--sidebar-background))',

\&#x20; 				foreground: 'hsl(var(--sidebar-foreground))',

\&#x20; 				primary: 'hsl(var(--sidebar-primary))',

\&#x20; 				'primary-foreground': 'hsl(var(--sidebar-primary-foreground))',

\&#x20; 				accent: 'hsl(var(--sidebar-accent))',

\&#x20; 				'accent-foreground': 'hsl(var(--sidebar-accent-foreground))',

\&#x20; 				border: 'hsl(var(--sidebar-border))',

\&#x20; 				ring: 'hsl(var(--sidebar-ring))'

\&#x20; 			}

\&#x20; 		},

\&#x20; 		keyframes: {

\&#x20; 			'accordion-down': {

\&#x20; 				from: { height: '0' },

\&#x20; 				to: { height: 'var(--radix-accordion-content-height)' }

\&#x20; 			},

\&#x20; 			'accordion-up': {

\&#x20; 				from: { height: 'var(--radix-accordion-content-height)' },

\&#x20; 				to: { height: '0' }

\&#x20; 			}

\&#x20; 		},

\&#x20; 		animation: {

\&#x20; 			'accordion-down': 'accordion-down 0.2s ease-out',

\&#x20; 			'accordion-up': 'accordion-up 0.2s ease-out'

\&#x20; 		}

\&#x20; 	}

\&#x20; },

\&#x20; plugins: \\\[require("tailwindcss-animate")],

}

```



\---



\## App.jsx



```jsx

import { Toaster } from "@/components/ui/toaster"

import { QueryClientProvider } from '@tanstack/react-query'

import { queryClientInstance } from '@/lib/query-client'

import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

import PageNotFound from './lib/PageNotFound';

import { AuthProvider, useAuth } from '@/lib/AuthContext';

import UserNotRegisteredError from '@/components/UserNotRegisteredError';

// Add page imports here

import Builder from './pages/Builder';



const AuthenticatedApp = () => {

\&#x20; const { isLoadingAuth, isLoadingPublicSettings, authError, navigateToLogin } = useAuth();



\&#x20; if (isLoadingPublicSettings || isLoadingAuth) {

\&#x20;   return (

\&#x20;     <div className="fixed inset-0 flex items-center justify-center">

\&#x20;       <div className="w-8 h-8 border-4 border-slate-200 border-t-slate-800 rounded-full animate-spin"></div>

\&#x20;     </div>

\&#x20;   );

\&#x20; }



\&#x20; if (authError) {

\&#x20;   if (authError.type === 'user\\\_not\\\_registered') {

\&#x20;     return <UserNotRegisteredError />;

\&#x20;   } else if (authError.type === 'auth\\\_required') {

\&#x20;     navigateToLogin();

\&#x20;     return null;

\&#x20;   }

\&#x20; }



\&#x20; return (

\&#x20;   <Routes>

\&#x20;     <Route path="/" element={<Builder />} />

\&#x20;     <Route path="/builder" element={<Builder />} />

\&#x20;     <Route path="\\\*" element={<PageNotFound />} />

\&#x20;   </Routes>

\&#x20; );

};



function App() {

\&#x20; return (

\&#x20;   <AuthProvider>

\&#x20;     <QueryClientProvider client={queryClientInstance}>

\&#x20;       <Router>

\&#x20;         <AuthenticatedApp />

\&#x20;       </Router>

\&#x20;       <Toaster />

\&#x20;     </QueryClientProvider>

\&#x20;   </AuthProvider>

\&#x20; )

}



export default App

```



\---



\## pages/Builder.jsx



```jsx

import React, { useState } from 'react';

import { useBuilder } from '@/hooks/useBuilder';

import FileExplorer from '@/components/builder/FileExplorer';

import CodeEditor from '@/components/builder/CodeEditor';

import LivePreview from '@/components/builder/LivePreview';

import AIChat from '@/components/builder/AIChat';

import Terminal from '@/components/builder/Terminal';

import { Code2, Eye, MessageSquare, TerminalSquare, PanelLeftClose, PanelLeftOpen } from 'lucide-react';



const PANEL\\\_TABS = \\\[

\&#x20; { id: 'editor', label: 'Editor', icon: Code2 },

\&#x20; { id: 'preview', label: 'Preview', icon: Eye },

\&#x20; { id: 'ai', label: 'AI', icon: MessageSquare },

\&#x20; { id: 'terminal', label: 'Terminal', icon: TerminalSquare },

];



export default function Builder() {

\&#x20; const urlParams = new URLSearchParams(window.location.search);

\&#x20; const projectId = urlParams.get('id') || null;



\&#x20; const builder = useBuilder({ projectId });



\&#x20; const \\\[sidebarOpen, setSidebarOpen] = useState(true);

\&#x20; const \\\[activeTab, setActiveTab] = useState('editor');

\&#x20; const \\\[terminalOpen, setTerminalOpen] = useState(false);



\&#x20; return (

\&#x20;   <div className="flex flex-col h-screen bg-\\\[#0a0a12] text-slate-200 overflow-hidden select-none">



\&#x20;     {/\\\* ── Top bar ── \\\*/}

\&#x20;     <header className="flex items-center gap-3 px-4 py-2 border-b border-\\\[#1e1e2e] bg-\\\[#0f0f17] shrink-0 z-10">

\&#x20;       <button

\&#x20;         onClick={() => setSidebarOpen(p => !p)}

\&#x20;         className="text-slate-500 hover:text-slate-200 transition-colors"

\&#x20;         title="Toggle file explorer"

\&#x20;       >

\&#x20;         {sidebarOpen ? <PanelLeftClose size={16} /> : <PanelLeftOpen size={16} />}

\&#x20;       </button>



\&#x20;       <span className="text-sm font-semibold text-slate-200 truncate max-w-\\\[180px]">

\&#x20;         {builder.project.name}

\&#x20;       </span>



\&#x20;       <span className={`text-\\\[10px] px-2 py-0.5 rounded-full font-medium ${

\&#x20;         builder.syncStatus === 'syncing' ? 'bg-yellow-500/20 text-yellow-400' :

\&#x20;         builder.syncStatus === 'saved'   ? 'bg-emerald-500/20 text-emerald-400' :

\&#x20;                                            'bg-slate-700 text-slate-500'

\&#x20;       }`}>

\&#x20;         {builder.syncStatus === 'syncing' ? 'syncing' : builder.syncStatus === 'saved' ? 'saved' : 'unsaved'}

\&#x20;       </span>



\&#x20;       {builder.isDirty \\\&\\\& (

\&#x20;         <span className="text-\\\[10px] text-yellow-400 ml-1">● unsaved changes</span>

\&#x20;       )}



\&#x20;       <div className="ml-auto flex gap-1">

\&#x20;         {PANEL\\\_TABS.map(tab => {

\&#x20;           const Icon = tab.icon;

\&#x20;           return (

\&#x20;             <button

\&#x20;               key={tab.id}

\&#x20;               onClick={() => setActiveTab(tab.id)}

\&#x20;               title={tab.label}

\&#x20;               className={`flex items-center gap-1.5 px-3 py-1 rounded text-xs transition-colors ${

\&#x20;                 activeTab === tab.id

\&#x20;                   ? 'bg-\\\[#1e1e2e] text-violet-300'

\&#x20;                   : 'text-slate-500 hover:text-slate-300'

\&#x20;               }`}

\&#x20;             >

\&#x20;               <Icon size={13} />

\&#x20;               <span className="hidden sm:inline">{tab.label}</span>

\&#x20;             </button>

\&#x20;           );

\&#x20;         })}

\&#x20;         <button

\&#x20;           onClick={() => setTerminalOpen(p => !p)}

\&#x20;           className={`flex items-center gap-1.5 px-3 py-1 rounded text-xs transition-colors ml-1 ${

\&#x20;             terminalOpen ? 'bg-emerald-600/20 text-emerald-400' : 'text-slate-500 hover:text-slate-300'

\&#x20;           }`}

\&#x20;           title="Toggle terminal"

\&#x20;         >

\&#x20;           <TerminalSquare size={13} />

\&#x20;           <span className="hidden sm:inline">Terminal</span>

\&#x20;         </button>

\&#x20;       </div>

\&#x20;     </header>



\&#x20;     {/\\\* ── Main workspace ── \\\*/}

\&#x20;     <div className="flex flex-1 min-h-0">



\&#x20;       {sidebarOpen \\\&\\\& (

\&#x20;         <FileExplorer

\&#x20;           files={builder.project.files}

\&#x20;           activeFilePath={builder.activeFilePath}

\&#x20;           onSelect={builder.setActiveFilePath}

\&#x20;           onAdd={builder.addFile}

\&#x20;           onDelete={builder.deleteFile}

\&#x20;           projectName={builder.project.name}

\&#x20;           syncStatus={builder.syncStatus}

\&#x20;         />

\&#x20;       )}



\&#x20;       <div className={`flex flex-col flex-1 min-w-0 min-h-0 ${activeTab !== 'editor' ? 'hidden lg:flex' : 'flex'}`}>

\&#x20;         <div className="flex-1 min-h-0 flex">

\&#x20;           <CodeEditor

\&#x20;             file={builder.activeFile}

\&#x20;             onChange={(content) => builder.updateFileContent(builder.activeFilePath, content)}

\&#x20;             isDirty={builder.isDirty}

\&#x20;           />

\&#x20;         </div>

\&#x20;         {terminalOpen \\\&\\\& (

\&#x20;           <div className="h-52 border-t border-\\\[#1e1e2e] shrink-0">

\&#x20;             <Terminal

\&#x20;               errors={builder.errors}

\&#x20;               onClear={builder.clearErrors}

\&#x20;             />

\&#x20;           </div>

\&#x20;         )}

\&#x20;       </div>



\&#x20;       <div className={`flex flex-col border-l border-\\\[#1e1e2e] min-w-0 ${

\&#x20;         activeTab === 'editor' ? 'hidden lg:flex lg:w-\\\[45%]' : 'flex flex-1'

\&#x20;       }`}>

\&#x20;         <div className={`flex-1 min-h-0 ${activeTab === 'ai' ? 'hidden' : 'flex flex-col'}`}>

\&#x20;           <LivePreview

\&#x20;             previewHTML={builder.previewHTML}

\&#x20;             isCompiling={builder.isCompiling}

\&#x20;             compileErrors={builder.compileErrors}

\&#x20;             onRefresh={builder.forceRefresh}

\&#x20;           />

\&#x20;         </div>



\&#x20;         {activeTab !== 'ai' \\\&\\\& (

\&#x20;           <div className="border-t border-\\\[#1e1e2e] shrink-0" />

\&#x20;         )}



\&#x20;         <div className={`shrink-0 border-t border-\\\[#1e1e2e] ${

\&#x20;           activeTab === 'ai' ? 'flex-1' : 'h-72'

\&#x20;         }`}>

\&#x20;           <AIChat

\&#x20;             onSend={builder.runAI}

\&#x20;             isGenerating={builder.isGenerating}

\&#x20;             lastMessage={builder.lastAIMessage}

\&#x20;             generationError={builder.generationError}

\&#x20;             files={builder.project.files}

\&#x20;             activeFilePath={builder.activeFilePath}

\&#x20;           />

\&#x20;         </div>

\&#x20;       </div>



\&#x20;     </div>

\&#x20;   </div>

\&#x20; );

}

```



\---



\## components/builder/FileExplorer.jsx



```jsx

import React, { useState } from 'react';

import { FilePlus, Trash2, ChevronRight, FileCode, FileText, File } from 'lucide-react';



function fileIcon(path) {

\&#x20; const ext = path.split('.').pop()?.toLowerCase();

\&#x20; if (\\\['jsx', 'tsx', 'js', 'ts'].includes(ext)) return <FileCode size={13} className="text-sky-400 shrink-0" />;

\&#x20; if (ext === 'css') return <FileText size={13} className="text-pink-400 shrink-0" />;

\&#x20; return <File size={13} className="text-slate-400 shrink-0" />;

}



export default function FileExplorer({ files, activeFilePath, onSelect, onAdd, onDelete, projectName, syncStatus }) {

\&#x20; const \\\[hovered, setHovered] = useState(null);



\&#x20; const handleAdd = () => {

\&#x20;   const name = window.prompt('File name (e.g. components/Button.jsx):');

\&#x20;   if (name?.trim()) onAdd(name.trim());

\&#x20; };



\&#x20; const handleDelete = (e, path) => {

\&#x20;   e.stopPropagation();

\&#x20;   if (window.confirm(`Delete ${path}?`)) onDelete(path);

\&#x20; };



\&#x20; return (

\&#x20;   <div className="flex flex-col h-full bg-\\\[#0f0f17] border-r border-\\\[#1e1e2e] w-52 shrink-0">

\&#x20;     <div className="px-3 py-2 border-b border-\\\[#1e1e2e] flex items-center justify-between">

\&#x20;       <span className="text-xs font-semibold text-slate-300 uppercase tracking-widest truncate">{projectName}</span>

\&#x20;       <button

\&#x20;         onClick={handleAdd}

\&#x20;         title="New file"

\&#x20;         className="text-slate-500 hover:text-violet-400 transition-colors ml-1 shrink-0"

\&#x20;       >

\&#x20;         <FilePlus size={14} />

\&#x20;       </button>

\&#x20;     </div>



\&#x20;     <div className="px-3 py-1 text-\\\[10px] text-slate-600 border-b border-\\\[#1e1e2e]">

\&#x20;       {syncStatus === 'syncing' \\\&\\\& <span className="text-yellow-500">⏳ syncing…</span>}

\&#x20;       {syncStatus === 'saved' \\\&\\\& <span className="text-emerald-500">✓ saved</span>}

\&#x20;       {syncStatus === 'idle' \\\&\\\& <span>not saved</span>}

\&#x20;     </div>



\&#x20;     <div className="flex-1 overflow-y-auto py-1">

\&#x20;       {files.map(f => (

\&#x20;         <div

\&#x20;           key={f.path}

\&#x20;           onClick={() => onSelect(f.path)}

\&#x20;           onMouseEnter={() => setHovered(f.path)}

\&#x20;           onMouseLeave={() => setHovered(null)}

\&#x20;           className={`flex items-center gap-1.5 px-3 py-\\\[5px] cursor-pointer text-xs group transition-colors ${

\&#x20;             activeFilePath === f.path

\&#x20;               ? 'bg-\\\[#1e1e2e] text-violet-300'

\&#x20;               : 'text-slate-400 hover:bg-\\\[#161622] hover:text-slate-200'

\&#x20;           }`}

\&#x20;         >

\&#x20;           <ChevronRight size={10} className="text-slate-600 shrink-0" />

\&#x20;           {fileIcon(f.path)}

\&#x20;           <span className="truncate flex-1">{f.path}</span>

\&#x20;           {hovered === f.path \\\&\\\& (

\&#x20;             <button

\&#x20;               onClick={e => handleDelete(e, f.path)}

\&#x20;               className="text-slate-600 hover:text-red-400 transition-colors shrink-0"

\&#x20;             >

\&#x20;               <Trash2 size={11} />

\&#x20;             </button>

\&#x20;           )}

\&#x20;         </div>

\&#x20;       ))}

\&#x20;     </div>

\&#x20;   </div>

\&#x20; );

}

```



\---



\## components/builder/CodeEditor.jsx



```jsx

import React, { useRef, useEffect } from 'react';

import { Circle } from 'lucide-react';



export default function CodeEditor({ file, onChange, isDirty }) {

\&#x20; const textareaRef = useRef(null);



\&#x20; useEffect(() => {

\&#x20;   if (textareaRef.current) textareaRef.current.scrollTop = 0;

\&#x20; }, \\\[file?.path]);



\&#x20; const handleKeyDown = (e) => {

\&#x20;   if (e.key === 'Tab') {

\&#x20;     e.preventDefault();

\&#x20;     const el = e.target;

\&#x20;     const start = el.selectionStart;

\&#x20;     const end = el.selectionEnd;

\&#x20;     const newValue = el.value.substring(0, start) + '  ' + el.value.substring(end);

\&#x20;     onChange(newValue);

\&#x20;     requestAnimationFrame(() => {

\&#x20;       el.selectionStart = el.selectionEnd = start + 2;

\&#x20;     });

\&#x20;   }

\&#x20; };



\&#x20; if (!file) {

\&#x20;   return (

\&#x20;     <div className="flex-1 flex items-center justify-center bg-\\\[#12121c] text-slate-600 text-sm select-none">

\&#x20;       Select a file to edit

\&#x20;     </div>

\&#x20;   );

\&#x20; }



\&#x20; return (

\&#x20;   <div className="flex flex-col flex-1 min-h-0 bg-\\\[#12121c]">

\&#x20;     <div className="flex items-center gap-1 px-3 py-1 bg-\\\[#0f0f17] border-b border-\\\[#1e1e2e] text-xs shrink-0">

\&#x20;       <span className="bg-\\\[#1e1e2e] text-slate-300 px-3 py-1 rounded-t flex items-center gap-1.5">

\&#x20;         {file.path.split('/').pop()}

\&#x20;         {isDirty \\\&\\\& <Circle size={6} fill="#f9e2af" stroke="none" />}

\&#x20;       </span>

\&#x20;     </div>



\&#x20;     <div className="flex flex-1 min-h-0 font-mono text-\\\[13px] leading-\\\[1.6]">

\&#x20;       <div

\&#x20;         className="select-none text-right text-slate-700 bg-\\\[#0f0f17] px-3 pt-3 pb-3 shrink-0 overflow-hidden"

\&#x20;         style={{ minWidth: 44 }}

\&#x20;         aria-hidden

\&#x20;       >

\&#x20;         {(file.content || '').split('\\\\n').map((\\\_, i) => (

\&#x20;           <div key={i}>{i + 1}</div>

\&#x20;         ))}

\&#x20;       </div>



\&#x20;       <textarea

\&#x20;         ref={textareaRef}

\&#x20;         value={file.content || ''}

\&#x20;         onChange={e => onChange(e.target.value)}

\&#x20;         onKeyDown={handleKeyDown}

\&#x20;         spellCheck={false}

\&#x20;         autoCorrect="off"

\&#x20;         autoCapitalize="off"

\&#x20;         className="flex-1 bg-transparent text-slate-100 resize-none outline-none pt-3 pb-3 pr-4 pl-2 overflow-auto"

\&#x20;         style={{ caretColor: '#cba6f7' }}

\&#x20;       />

\&#x20;     </div>

\&#x20;   </div>

\&#x20; );

}

```



\---



\## components/builder/LivePreview.jsx



```jsx

import React, { useRef, useEffect } from 'react';

import { RefreshCw, Loader2, AlertTriangle } from 'lucide-react';

import { injectErrorRelay, getSandboxAttributes } from '@/lib/previewSandbox';



export default function LivePreview({ previewHTML, isCompiling, compileErrors, onRefresh }) {

\&#x20; const iframeRef = useRef(null);



\&#x20; useEffect(() => {

\&#x20;   if (!iframeRef.current || !previewHTML) return;

\&#x20;   iframeRef.current.srcdoc = injectErrorRelay(previewHTML);

\&#x20; }, \\\[previewHTML]);



\&#x20; return (

\&#x20;   <div className="flex flex-col h-full bg-\\\[#0f0f17]">

\&#x20;     <div className="flex items-center gap-2 px-3 py-1.5 border-b border-\\\[#1e1e2e] bg-\\\[#0f0f17] shrink-0">

\&#x20;       <span className="text-\\\[11px] font-semibold text-slate-500 uppercase tracking-widest">Preview</span>

\&#x20;       {isCompiling \\\&\\\& <Loader2 size={11} className="text-sky-400 animate-spin" />}

\&#x20;       {compileErrors.length > 0 \\\&\\\& (

\&#x20;         <span className="flex items-center gap-1 text-\\\[11px] text-red-400">

\&#x20;           <AlertTriangle size={11} /> {compileErrors.length} error{compileErrors.length > 1 ? 's' : ''}

\&#x20;         </span>

\&#x20;       )}

\&#x20;       <button

\&#x20;         onClick={onRefresh}

\&#x20;         className="ml-auto text-slate-600 hover:text-slate-300 transition-colors"

\&#x20;         title="Force refresh"

\&#x20;       >

\&#x20;         <RefreshCw size={12} />

\&#x20;       </button>

\&#x20;     </div>



\&#x20;     <iframe

\&#x20;       ref={iframeRef}

\&#x20;       title="live-preview"

\&#x20;       sandbox={getSandboxAttributes()}

\&#x20;       className="flex-1 w-full bg-white border-none"

\&#x20;     />

\&#x20;   </div>

\&#x20; );

}

```



\---



\## components/builder/AIChat.jsx



```jsx

import React, { useState, useRef, useEffect } from 'react';

import { Send, Loader2, Bot, User, Sparkles, AlertCircle } from 'lucide-react';



export default function AIChat({ onSend, isGenerating, lastMessage, generationError, files, activeFilePath }) {

\&#x20; const \\\[input, setInput] = useState('');

\&#x20; const \\\[mode, setMode] = useState('edit'); // edit | create | refactor | debug

\&#x20; const \\\[chatHistory, setChatHistory] = useState(\\\[

\&#x20;   { role: 'assistant', content: 'Hi! I can edit your code, create new components, refactor, or debug. What would you like to do?' }

\&#x20; ]);

\&#x20; const bottomRef = useRef(null);



\&#x20; useEffect(() => {

\&#x20;   if (lastMessage) {

\&#x20;     setChatHistory(prev => \\\[...prev, { role: 'assistant', content: lastMessage }]);

\&#x20;   }

\&#x20; }, \\\[lastMessage]);



\&#x20; useEffect(() => {

\&#x20;   if (generationError) {

\&#x20;     setChatHistory(prev => \\\[...prev, { role: 'assistant', content: `⚠️ ${generationError}`, isError: true }]);

\&#x20;   }

\&#x20; }, \\\[generationError]);



\&#x20; useEffect(() => {

\&#x20;   bottomRef.current?.scrollIntoView({ behavior: 'smooth' });

\&#x20; }, \\\[chatHistory, isGenerating]);



\&#x20; const handleSubmit = (e) => {

\&#x20;   e.preventDefault();

\&#x20;   if (!input.trim() || isGenerating) return;

\&#x20;   const prompt = input.trim();

\&#x20;   setChatHistory(prev => \\\[...prev, { role: 'user', content: prompt }]);

\&#x20;   setInput('');

\&#x20;   onSend(prompt, mode, null);

\&#x20; };



\&#x20; const MODES = \\\['edit', 'create', 'refactor', 'debug'];



\&#x20; return (

\&#x20;   <div className="flex flex-col h-full bg-\\\[#0f0f17]">

\&#x20;     <div className="flex items-center gap-2 px-3 py-1.5 border-b border-\\\[#1e1e2e] shrink-0">

\&#x20;       <Sparkles size={13} className="text-violet-400" />

\&#x20;       <span className="text-\\\[11px] font-semibold text-slate-400 uppercase tracking-widest">AI Assistant</span>

\&#x20;       <div className="ml-auto flex gap-1">

\&#x20;         {MODES.map(m => (

\&#x20;           <button

\&#x20;             key={m}

\&#x20;             onClick={() => setMode(m)}

\&#x20;             className={`text-\\\[10px] px-2 py-0.5 rounded transition-colors ${

\&#x20;               mode === m

\&#x20;                 ? 'bg-violet-600 text-white'

\&#x20;                 : 'text-slate-500 hover:text-slate-300'

\&#x20;             }`}

\&#x20;           >

\&#x20;             {m}

\&#x20;           </button>

\&#x20;         ))}

\&#x20;       </div>

\&#x20;     </div>



\&#x20;     <div className="flex-1 overflow-y-auto p-3 space-y-3 min-h-0">

\&#x20;       {chatHistory.map((msg, i) => (

\&#x20;         <div key={i} className={`flex gap-2 ${msg.role === 'user' ? 'flex-row-reverse' : ''}`}>

\&#x20;           <div className={`shrink-0 w-6 h-6 rounded-full flex items-center justify-center ${

\&#x20;             msg.role === 'user' ? 'bg-violet-600' : 'bg-\\\[#1e1e2e]'

\&#x20;           }`}>

\&#x20;             {msg.role === 'user'

\&#x20;               ? <User size={12} className="text-white" />

\&#x20;               : <Bot size={12} className="text-violet-400" />

\&#x20;             }

\&#x20;           </div>

\&#x20;           <div className={`max-w-\\\[80%] text-\\\[12px] leading-relaxed px-3 py-2 rounded-xl ${

\&#x20;             msg.role === 'user'

\&#x20;               ? 'bg-violet-600/20 text-violet-200 rounded-tr-sm'

\&#x20;               : msg.isError

\&#x20;                 ? 'bg-red-500/10 text-red-400 rounded-tl-sm'

\&#x20;                 : 'bg-\\\[#1e1e2e] text-slate-300 rounded-tl-sm'

\&#x20;           }`}>

\&#x20;             {msg.content}

\&#x20;           </div>

\&#x20;         </div>

\&#x20;       ))}

\&#x20;       {isGenerating \\\&\\\& (

\&#x20;         <div className="flex gap-2">

\&#x20;           <div className="w-6 h-6 rounded-full bg-\\\[#1e1e2e] flex items-center justify-center shrink-0">

\&#x20;             <Bot size={12} className="text-violet-400" />

\&#x20;           </div>

\&#x20;           <div className="bg-\\\[#1e1e2e] text-slate-400 text-\\\[12px] px-3 py-2 rounded-xl rounded-tl-sm flex items-center gap-2">

\&#x20;             <Loader2 size={11} className="animate-spin text-violet-400" />

\&#x20;             Generating…

\&#x20;           </div>

\&#x20;         </div>

\&#x20;       )}

\&#x20;       <div ref={bottomRef} />

\&#x20;     </div>



\&#x20;     {activeFilePath \\\&\\\& (

\&#x20;       <div className="px-3 py-1 text-\\\[10px] text-slate-600 border-t border-\\\[#1e1e2e] bg-\\\[#0a0a12]">

\&#x20;         Context: <span className="text-slate-500">{activeFilePath}</span>

\&#x20;       </div>

\&#x20;     )}



\&#x20;     <form onSubmit={handleSubmit} className="flex gap-2 p-2 border-t border-\\\[#1e1e2e] bg-\\\[#0a0a12] shrink-0">

\&#x20;       <input

\&#x20;         value={input}

\&#x20;         onChange={e => setInput(e.target.value)}

\&#x20;         placeholder={isGenerating ? 'Generating…' : `${mode} — describe what you want…`}

\&#x20;         disabled={isGenerating}

\&#x20;         className="flex-1 bg-\\\[#1e1e2e] text-slate-200 text-\\\[12px] rounded-lg px-3 py-2 outline-none placeholder:text-slate-600 border border-\\\[#2a2a3e] focus:border-violet-600 transition-colors"

\&#x20;       />

\&#x20;       <button

\&#x20;         type="submit"

\&#x20;         disabled={isGenerating || !input.trim()}

\&#x20;         className="bg-violet-600 hover:bg-violet-500 disabled:opacity-40 text-white rounded-lg px-3 py-2 transition-colors flex items-center"

\&#x20;       >

\&#x20;         <Send size={13} />

\&#x20;       </button>

\&#x20;     </form>

\&#x20;   </div>

\&#x20; );

}

```



\---



\## components/builder/Terminal.jsx



```jsx

import React, { useEffect, useRef, useState } from 'react';

import { Terminal as TermIcon, Trash2, ChevronRight } from 'lucide-react';



export default function Terminal({ errors, onClear }) {

\&#x20; const \\\[consoleLogs, setConsoleLogs] = useState(\\\[]);

\&#x20; const bottomRef = useRef(null);



\&#x20; useEffect(() => {

\&#x20;   const handler = (event) => {

\&#x20;     if (event.data?.type === 'PREVIEW\\\_CONSOLE') {

\&#x20;       const { level, args } = event.data;

\&#x20;       setConsoleLogs(prev => \\\[

\&#x20;         ...prev,

\&#x20;         { level, text: args.join(' '), timestamp: Date.now() }

\&#x20;       ].slice(-200));

\&#x20;     }

\&#x20;   };

\&#x20;   window.addEventListener('message', handler);

\&#x20;   return () => window.removeEventListener('message', handler);

\&#x20; }, \\\[]);



\&#x20; useEffect(() => {

\&#x20;   bottomRef.current?.scrollIntoView({ behavior: 'smooth' });

\&#x20; }, \\\[consoleLogs, errors]);



\&#x20; const handleClear = () => {

\&#x20;   setConsoleLogs(\\\[]);

\&#x20;   onClear();

\&#x20; };



\&#x20; const levelColor = {

\&#x20;   log: 'text-slate-300',

\&#x20;   warn: 'text-yellow-400',

\&#x20;   error: 'text-red-400'

\&#x20; };



\&#x20; const allEntries = \\\[

\&#x20;   ...errors.map(e => ({ isError: true, source: e.source, message: e.message, file: e.file\\\_path, timestamp: e.timestamp })),

\&#x20;   ...consoleLogs.map(l => ({ isLog: true, level: l.level, text: l.text, timestamp: l.timestamp }))

\&#x20; ].sort((a, b) => (a.timestamp || 0) - (b.timestamp || 0));



\&#x20; return (

\&#x20;   <div className="flex flex-col h-full bg-\\\[#080810]">

\&#x20;     <div className="flex items-center gap-2 px-3 py-1.5 border-b border-\\\[#1e1e2e] shrink-0">

\&#x20;       <TermIcon size={12} className="text-emerald-400" />

\&#x20;       <span className="text-\\\[11px] font-semibold text-slate-500 uppercase tracking-widest">Terminal</span>

\&#x20;       <button

\&#x20;         onClick={handleClear}

\&#x20;         className="ml-auto text-slate-700 hover:text-slate-400 transition-colors"

\&#x20;         title="Clear"

\&#x20;       >

\&#x20;         <Trash2 size={11} />

\&#x20;       </button>

\&#x20;     </div>



\&#x20;     <div className="flex-1 overflow-y-auto p-3 font-mono text-\\\[11px] leading-relaxed space-y-0.5">

\&#x20;       {allEntries.length === 0 \\\&\\\& (

\&#x20;         <div className="text-slate-700 italic">No output yet. Console logs and errors will appear here.</div>

\&#x20;       )}

\&#x20;       {allEntries.map((entry, i) => (

\&#x20;         <div key={i} className="flex gap-2">

\&#x20;           <ChevronRight size={10} className="text-slate-700 shrink-0 mt-0.5" />

\&#x20;           {entry.isError ? (

\&#x20;             <span className="text-red-400">

\&#x20;               \\\[{entry.source}] {entry.file \\\&\\\& <span className="text-orange-400">{entry.file}: </span>}{entry.message}

\&#x20;             </span>

\&#x20;           ) : (

\&#x20;             <span className={levelColor\\\[entry.level] || 'text-slate-300'}>

\&#x20;               {entry.level !== 'log' \\\&\\\& <span className="text-slate-600">\\\[{entry.level}] </span>}

\&#x20;               {entry.text}

\&#x20;             </span>

\&#x20;           )}

\&#x20;         </div>

\&#x20;       ))}

\&#x20;       <div ref={bottomRef} />

\&#x20;     </div>



\&#x20;     <div className="px-3 py-1.5 border-t border-\\\[#1e1e2e] flex items-center gap-2 text-\\\[11px] font-mono text-slate-700">

\&#x20;       <span className="text-emerald-500">$</span>

\&#x20;       <span className="text-slate-600 italic">preview sandbox — read-only console</span>

\&#x20;     </div>

\&#x20;   </div>

\&#x20; );

}

```



\---



\## hooks/useBuilder.js



```js

import { useEffect, useCallback } from 'react';

import { useProjectState } from './useProjectState';

import { useCloudSync } from './useCloudSync';

import { useLivePreview } from './useLivePreview';

import { useAIGeneration } from './useAIGeneration';

import { useErrorTracker } from './useErrorTracker';



export function useBuilder({ projectId = null } = {}) {

\&#x20; const projectState = useProjectState();

\&#x20; const cloudSync = useCloudSync();

\&#x20; const livePreview = useLivePreview(

\&#x20;   projectState.project.files,

\&#x20;   projectState.project.entry\\\_file

\&#x20; );

\&#x20; const aiGen = useAIGeneration();

\&#x20; const errorTracker = useErrorTracker(projectState.project.id);



\&#x20; useEffect(() => {

\&#x20;   if (!projectId) return;

\&#x20;   cloudSync.loadProject(projectId).then(project => {

\&#x20;     projectState.applyProjectSnapshot(project);

\&#x20;   });

\&#x20; }, \\\[projectId]); // eslint-disable-line react-hooks/exhaustive-deps



\&#x20; useEffect(() => {

\&#x20;   if (!projectState.isDirty) return;

\&#x20;   cloudSync.saveProject(projectState.project).then(saved => {

\&#x20;     if (saved?.id \\\&\\\& !projectState.project.id) {

\&#x20;       projectState.applyProjectSnapshot({ ...projectState.project, id: saved.id });

\&#x20;     } else {

\&#x20;       projectState.markClean();

\&#x20;     }

\&#x20;   });

\&#x20; }, \\\[projectState.project, projectState.isDirty]); // eslint-disable-line react-hooks/exhaustive-deps



\&#x20; useEffect(() => {

\&#x20;   livePreview.compileErrors.forEach(err => errorTracker.addCompileError(err));

\&#x20; }, \\\[livePreview.compileErrors]); // eslint-disable-line react-hooks/exhaustive-deps



\&#x20; useEffect(() => {

\&#x20;   const handler = (event) => {

\&#x20;     if (event.data?.type === 'PREVIEW\\\_RUNTIME\\\_ERROR') {

\&#x20;       errorTracker.addRuntimeError(event.data.error);

\&#x20;     }

\&#x20;   };

\&#x20;   window.addEventListener('message', handler);

\&#x20;   return () => window.removeEventListener('message', handler);

\&#x20; }, \\\[errorTracker]);



\&#x20; const runAI = useCallback((prompt, mode = 'edit', targetFile = null) => {

\&#x20;   aiGen.generate(

\&#x20;     {

\&#x20;       prompt,

\&#x20;       currentFiles: projectState.project.files,

\&#x20;       targetFile,

\&#x20;       mode

\&#x20;     },

\&#x20;     (newFiles) => {

\&#x20;       newFiles.forEach(f => {

\&#x20;         const existing = projectState.project.files.find(ef => ef.path === f.path);

\&#x20;         if (!existing) {

\&#x20;           projectState.addFile(f.path, f.content);

\&#x20;         } else {

\&#x20;           projectState.updateFileContent(f.path, f.content);

\&#x20;         }

\&#x20;       });

\&#x20;     }

\&#x20;   );

\&#x20; }, \\\[aiGen, projectState]);



\&#x20; const saveNow = useCallback(async () => {

\&#x20;   const saved = await cloudSync.saveProject(projectState.project, { immediate: true });

\&#x20;   projectState.markClean();

\&#x20;   return saved;

\&#x20; }, \\\[cloudSync, projectState]);



\&#x20; const newProject = useCallback((name = 'Untitled Project') => {

\&#x20;   projectState.applyProjectSnapshot({

\&#x20;     id: null,

\&#x20;     name,

\&#x20;     entry\\\_file: 'App.jsx',

\&#x20;     files: \\\[],

\&#x20;     status: 'active'

\&#x20;   });

\&#x20;   errorTracker.clearErrors();

\&#x20; }, \\\[projectState, errorTracker]);



\&#x20; return {

\&#x20;   ...projectState,

\&#x20;   previewHTML: livePreview.previewHTML,

\&#x20;   compileErrors: livePreview.compileErrors,

\&#x20;   isCompiling: livePreview.isCompiling,

\&#x20;   forceRefresh: livePreview.forceRefresh,

\&#x20;   runAI,

\&#x20;   isGenerating: aiGen.isGenerating,

\&#x20;   generationError: aiGen.generationError,

\&#x20;   lastAIMessage: aiGen.lastMessage,

\&#x20;   errors: errorTracker.errors,

\&#x20;   addRuntimeError: errorTracker.addRuntimeError,

\&#x20;   addLog: errorTracker.addLog,

\&#x20;   clearErrors: errorTracker.clearErrors,

\&#x20;   syncStatus: cloudSync.syncStatus,

\&#x20;   listProjects: cloudSync.listProjects,

\&#x20;   deleteProject: cloudSync.deleteProject,

\&#x20;   saveNow,

\&#x20;   newProject

\&#x20; };

}

```



\---



\## hooks/useProjectState.js



```js

import { useState, useCallback, useRef } from 'react';

import { upsertFile, removeFile, renameFile, findFile, createFile } from '@/lib/fileUtils';

import { DEFAULT\\\_PROJECT\\\_FILES } from '@/lib/constants';



export function useProjectState(initialProject = null) {

\&#x20; const \\\[project, setProject] = useState(() => initialProject || {

\&#x20;   id: null,

\&#x20;   name: 'Aura Dashboard',

\&#x20;   entry\\\_file: 'App.jsx',

\&#x20;   files: DEFAULT\\\_PROJECT\\\_FILES,

\&#x20;   status: 'active'

\&#x20; });



\&#x20; const \\\[activeFilePath, setActiveFilePath] = useState(

\&#x20;   initialProject?.entry\\\_file || 'App.jsx'

\&#x20; );



\&#x20; const \\\[isDirty, setIsDirty] = useState(false);

\&#x20; const undoStack = useRef({});



\&#x20; const updateFileContent = useCallback((path, content) => {

\&#x20;   setProject(prev => {

\&#x20;     const file = findFile(prev.files, path);

\&#x20;     if (!file) return prev;

\&#x20;     if (!undoStack.current\\\[path]) undoStack.current\\\[path] = \\\[];

\&#x20;     undoStack.current\\\[path].push(file.content);

\&#x20;     if (undoStack.current\\\[path].length > 50) undoStack.current\\\[path].shift();

\&#x20;     return { ...prev, files: upsertFile(prev.files, { ...file, content }) };

\&#x20;   });

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[]);



\&#x20; const undoFileEdit = useCallback((path) => {

\&#x20;   const stack = undoStack.current\\\[path];

\&#x20;   if (!stack || stack.length === 0) return;

\&#x20;   const prevContent = stack.pop();

\&#x20;   setProject(prev => {

\&#x20;     const file = findFile(prev.files, path);

\&#x20;     if (!file) return prev;

\&#x20;     return { ...prev, files: upsertFile(prev.files, { ...file, content: prevContent }) };

\&#x20;   });

\&#x20; }, \\\[]);



\&#x20; const addFile = useCallback((path, content = '') => {

\&#x20;   const newFile = createFile(path, content);

\&#x20;   setProject(prev => ({ ...prev, files: upsertFile(prev.files, newFile) }));

\&#x20;   setActiveFilePath(newFile.path);

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[]);



\&#x20; const deleteFile = useCallback((path) => {

\&#x20;   setProject(prev => {

\&#x20;     const updated = removeFile(prev.files, path);

\&#x20;     return { ...prev, files: updated };

\&#x20;   });

\&#x20;   setActiveFilePath(prev => {

\&#x20;     if (prev === path) {

\&#x20;       return project.files.find(f => f.path !== path)?.path || '';

\&#x20;     }

\&#x20;     return prev;

\&#x20;   });

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[project.files]);



\&#x20; const renameFileInProject = useCallback((oldPath, newPath) => {

\&#x20;   setProject(prev => {

\&#x20;     const updated = renameFile(prev.files, oldPath, newPath);

\&#x20;     const entryUpdated = prev.entry\\\_file === oldPath ? newPath : prev.entry\\\_file;

\&#x20;     return { ...prev, files: updated, entry\\\_file: entryUpdated };

\&#x20;   });

\&#x20;   setActiveFilePath(prev => prev === oldPath ? newPath : prev);

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[]);



\&#x20; const renameProject = useCallback((name) => {

\&#x20;   setProject(prev => ({ ...prev, name }));

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[]);



\&#x20; const setEntryFile = useCallback((path) => {

\&#x20;   setProject(prev => ({ ...prev, entry\\\_file: path }));

\&#x20;   setIsDirty(true);

\&#x20; }, \\\[]);



\&#x20; const applyProjectSnapshot = useCallback((snapshot) => {

\&#x20;   setProject(snapshot);

\&#x20;   setActiveFilePath(snapshot.entry\\\_file || snapshot.files?.\\\[0]?.path || '');

\&#x20;   setIsDirty(false);

\&#x20;   undoStack.current = {};

\&#x20; }, \\\[]);



\&#x20; const markClean = useCallback(() => setIsDirty(false), \\\[]);



\&#x20; const activeFile = findFile(project.files, activeFilePath);



\&#x20; return {

\&#x20;   project,

\&#x20;   activeFilePath,

\&#x20;   activeFile,

\&#x20;   isDirty,

\&#x20;   setActiveFilePath,

\&#x20;   updateFileContent,

\&#x20;   undoFileEdit,

\&#x20;   addFile,

\&#x20;   deleteFile,

\&#x20;   renameFile: renameFileInProject,

\&#x20;   renameProject,

\&#x20;   setEntryFile,

\&#x20;   applyProjectSnapshot,

\&#x20;   markClean

\&#x20; };

}

```



\---



\## hooks/useCloudSync.js



```js

import { useCallback, useEffect, useRef, useState } from 'react';

import { base44 } from '@/api/base44Client';

import { saveProjectLocally, loadProjectLocally } from '@/lib/localCache';

import { CLOUD\\\_SYNC\\\_DEBOUNCE\\\_MS } from '@/lib/constants';



export function useCloudSync() {

\&#x20; const \\\[syncStatus, setSyncStatus] = useState('idle');

\&#x20; const debounceTimer = useRef(null);



\&#x20; const saveProject = useCallback(async (project, { immediate = false } = {}) => {

\&#x20;   if (project.id) saveProjectLocally(project);



\&#x20;   if (debounceTimer.current) clearTimeout(debounceTimer.current);



\&#x20;   const doSave = async () => {

\&#x20;     setSyncStatus('syncing');

\&#x20;     const payload = {

\&#x20;       name: project.name,

\&#x20;       description: project.description || '',

\&#x20;       entry\\\_file: project.entry\\\_file,

\&#x20;       files: project.files,

\&#x20;       status: project.status || 'active',

\&#x20;       last\\\_synced\\\_at: new Date().toISOString()

\&#x20;     };



\&#x20;     let saved;

\&#x20;     if (project.id) {

\&#x20;       saved = await base44.entities.Project.update(project.id, payload);

\&#x20;     } else {

\&#x20;       saved = await base44.entities.Project.create(payload);

\&#x20;     }



\&#x20;     saveProjectLocally(saved);

\&#x20;     setSyncStatus('saved');

\&#x20;     return saved;

\&#x20;   };



\&#x20;   if (immediate) {

\&#x20;     return doSave();

\&#x20;   } else {

\&#x20;     return new Promise((resolve) => {

\&#x20;       debounceTimer.current = setTimeout(async () => {

\&#x20;         const result = await doSave();

\&#x20;         resolve(result);

\&#x20;       }, CLOUD\\\_SYNC\\\_DEBOUNCE\\\_MS);

\&#x20;     });

\&#x20;   }

\&#x20; }, \\\[]);



\&#x20; const loadProject = useCallback(async (projectId) => {

\&#x20;   const cached = loadProjectLocally(projectId);

\&#x20;   setSyncStatus('syncing');

\&#x20;   const cloud = await base44.entities.Project.filter({ id: projectId });

\&#x20;   const project = cloud?.\\\[0] || cached;

\&#x20;   if (!project) throw new Error(`Project ${projectId} not found.`);

\&#x20;   if (project.id) saveProjectLocally(project);

\&#x20;   setSyncStatus('saved');

\&#x20;   return project;

\&#x20; }, \\\[]);



\&#x20; const listProjects = useCallback(async () => {

\&#x20;   const projects = await base44.entities.Project.list('-updated\\\_date', 50);

\&#x20;   return projects;

\&#x20; }, \\\[]);



\&#x20; const deleteProject = useCallback(async (projectId) => {

\&#x20;   await base44.entities.Project.delete(projectId);

\&#x20; }, \\\[]);



\&#x20; useEffect(() => () => {

\&#x20;   if (debounceTimer.current) clearTimeout(debounceTimer.current);

\&#x20; }, \\\[]);



\&#x20; return { syncStatus, saveProject, loadProject, listProjects, deleteProject };

}

```



\---



\## hooks/useLivePreview.js



```js

import { useState, useEffect, useCallback, useRef } from 'react';

import { buildPreviewHTML } from '@/lib/babelCompiler';

import { PREVIEW\\\_DEBOUNCE\\\_MS } from '@/lib/constants';



export function useLivePreview(files, entryFile = 'App.jsx') {

\&#x20; const \\\[previewHTML, setPreviewHTML] = useState('');

\&#x20; const \\\[compileErrors, setCompileErrors] = useState(\\\[]);

\&#x20; const \\\[isCompiling, setIsCompiling] = useState(false);

\&#x20; const debounceTimer = useRef(null);



\&#x20; const compile = useCallback(async (currentFiles, currentEntry) => {

\&#x20;   setIsCompiling(true);

\&#x20;   setCompileErrors(\\\[]);



\&#x20;   const cssFiles = currentFiles

\&#x20;     .filter(f => f.path.endsWith('.css'))

\&#x20;     .map(f => f.path);



\&#x20;   const { html, errors } = await buildPreviewHTML(currentFiles, currentEntry, cssFiles);



\&#x20;   setPreviewHTML(html);

\&#x20;   setCompileErrors(errors || \\\[]);

\&#x20;   setIsCompiling(false);

\&#x20; }, \\\[]);



\&#x20; useEffect(() => {

\&#x20;   if (!files || files.length === 0) return;



\&#x20;   if (debounceTimer.current) clearTimeout(debounceTimer.current);

\&#x20;   debounceTimer.current = setTimeout(() => {

\&#x20;     compile(files, entryFile);

\&#x20;   }, PREVIEW\\\_DEBOUNCE\\\_MS);



\&#x20;   return () => {

\&#x20;     if (debounceTimer.current) clearTimeout(debounceTimer.current);

\&#x20;   };

\&#x20; }, \\\[files, entryFile, compile]);



\&#x20; const forceRefresh = useCallback(() => {

\&#x20;   if (debounceTimer.current) clearTimeout(debounceTimer.current);

\&#x20;   compile(files, entryFile);

\&#x20; }, \\\[files, entryFile, compile]);



\&#x20; return { previewHTML, compileErrors, isCompiling, forceRefresh };

}

```



\---



\## hooks/useAIGeneration.js



```js

import { useState, useCallback } from 'react';

import { runAIPipeline } from '@/lib/aiPipeline';



export function useAIGeneration() {

\&#x20; const \\\[isGenerating, setIsGenerating] = useState(false);

\&#x20; const \\\[generationError, setGenerationError] = useState(null);

\&#x20; const \\\[lastMessage, setLastMessage] = useState(null);



\&#x20; const generate = useCallback(async (request, onFilesUpdated) => {

\&#x20;   setIsGenerating(true);

\&#x20;   setGenerationError(null);

\&#x20;   setLastMessage(null);



\&#x20;   const result = await runAIPipeline(request);



\&#x20;   setIsGenerating(false);

\&#x20;   setLastMessage(result.message);



\&#x20;   if (result.error) {

\&#x20;     setGenerationError(result.error);

\&#x20;     return;

\&#x20;   }



\&#x20;   onFilesUpdated(result.files);

\&#x20; }, \\\[]);



\&#x20; const clearError = useCallback(() => setGenerationError(null), \\\[]);



\&#x20; return { generate, isGenerating, generationError, lastMessage, clearError };

}

```



\---



\## hooks/useErrorTracker.js



```js

import { useState, useCallback } from 'react';

import { base44 } from '@/api/base44Client';



export function useErrorTracker(projectId) {

\&#x20; const \\\[errors, setErrors] = useState(\\\[]);



\&#x20; const addCompileError = useCallback((err) => {

\&#x20;   const entry = {

\&#x20;     type: 'error',

\&#x20;     source: 'compile',

\&#x20;     file\\\_path: err.file,

\&#x20;     message: err.message,

\&#x20;     timestamp: Date.now()

\&#x20;   };

\&#x20;   setErrors(prev => \\\[entry, ...prev].slice(0, 100));

\&#x20; }, \\\[]);



\&#x20; const addRuntimeError = useCallback((err) => {

\&#x20;   const entry = {

\&#x20;     type: 'error',

\&#x20;     source: 'runtime',

\&#x20;     message: err.message,

\&#x20;     stack: err.stack,

\&#x20;     timestamp: Date.now()

\&#x20;   };

\&#x20;   setErrors(prev => \\\[entry, ...prev].slice(0, 100));



\&#x20;   if (projectId) {

\&#x20;     base44.entities.BuildLog.create({

\&#x20;       project\\\_id: projectId,

\&#x20;       type: 'error',

\&#x20;       message: err.message,

\&#x20;       stack: err.stack

\&#x20;     }).catch(() => {});

\&#x20;   }

\&#x20; }, \\\[projectId]);



\&#x20; const addLog = useCallback((type, message, filePath) => {

\&#x20;   const entry = { type, message, file\\\_path: filePath, source: 'system', timestamp: Date.now() };

\&#x20;   setErrors(prev => \\\[entry, ...prev].slice(0, 100));

\&#x20; }, \\\[]);



\&#x20; const clearErrors = useCallback(() => setErrors(\\\[]), \\\[]);



\&#x20; return { errors, addCompileError, addRuntimeError, addLog, clearErrors };

}

```



\---



\## lib/babelCompiler.js



```js

const BABEL\\\_CDN = 'https://unpkg.com/@babel/standalone/babel.min.js';



let babelLoaded = false;

const babelLoadPromise = loadBabel();



async function loadBabel() {

\&#x20; if (typeof window === 'undefined') return;

\&#x20; if (window.Babel) { babelLoaded = true; return; }

\&#x20; await new Promise((resolve, reject) => {

\&#x20;   const script = document.createElement('script');

\&#x20;   script.src = BABEL\\\_CDN;

\&#x20;   script.onload = () => { babelLoaded = true; resolve(); };

\&#x20;   script.onerror = reject;

\&#x20;   document.head.appendChild(script);

\&#x20; });

}



export function transformCode(source, filename = 'file.jsx') {

\&#x20; if (!window.Babel) throw new Error('Babel is not loaded yet.');

\&#x20; const result = window.Babel.transform(source, {

\&#x20;   filename,

\&#x20;   presets: \\\['react', 'env'],

\&#x20;   plugins: \\\[],

\&#x20;   sourceType: 'module'

\&#x20; });

\&#x20; return result.code;

}



export async function buildPreviewHTML(files, entryFile = 'App.jsx', cssFiles = \\\[]) {

\&#x20; await babelLoadPromise;



\&#x20; const errors = \\\[];

\&#x20; const transformedModules = {};



\&#x20; for (const file of files) {

\&#x20;   const ext = file.path.split('.').pop()?.toLowerCase();

\&#x20;   if (\\\['js', 'jsx', 'ts', 'tsx'].includes(ext)) {

\&#x20;     try {

\&#x20;       transformedModules\\\[file.path] = transformCode(file.content, file.path);

\&#x20;     } catch (err) {

\&#x20;       errors.push({ file: file.path, message: err.message });

\&#x20;       transformedModules\\\[file.path] = `/\\\* Compile error in ${file.path}: ${err.message} \\\*/`;

\&#x20;     }

\&#x20;   }

\&#x20; }



\&#x20; const cssContent = cssFiles

\&#x20;   .map(f => files.find(file => file.path === f)?.content || '')

\&#x20;   .join('\\\\n');



\&#x20; const moduleRegistry = Object.entries(transformedModules)

\&#x20;   .map((\\\[path, code]) => {

\&#x20;     const safePath = JSON.stringify(path);

\&#x20;     return `\\\_\\\_registry\\\[${safePath}] = (function(module, exports, require) {\\\\n${code}\\\\n})`;

\&#x20;   })

\&#x20;   .join(';\\\\n');



\&#x20; const entryCode = transformedModules\\\[entryFile] || '';



\&#x20; const html = `<!DOCTYPE html>

<html>

<head>

\&#x20; <meta charset="UTF-8" />

\&#x20; <meta name="viewport" content="width=device-width, initial-scale=1.0" />

\&#x20; <style>${cssContent}</style>

\&#x20; <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>

\&#x20; <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

</head>

<body>

\&#x20; <div id="root"></div>

\&#x20; <script>

\&#x20;   const \\\_\\\_registry = {};

\&#x20;   const \\\_\\\_moduleCache = {};



\&#x20;   function require(path) {

\&#x20;     if (\\\_\\\_moduleCache\\\[path]) return \\\_\\\_moduleCache\\\[path].exports;

\&#x20;     const mod = { exports: {} };

\&#x20;     \\\_\\\_moduleCache\\\[path] = mod;

\&#x20;     if (\\\_\\\_registry\\\[path]) {

\&#x20;       \\\_\\\_registry\\\[path](mod, mod.exports, require);

\&#x20;     }

\&#x20;     return mod.exports;

\&#x20;   }



\&#x20;   const React = window.React;

\&#x20;   const ReactDOM = window.ReactDOM;



\&#x20;   try {

\&#x20;     ${moduleRegistry};

\&#x20;     const \\\_\\\_entryMod = { exports: {} };

\&#x20;     (function(module, exports, require) {

\&#x20;       ${entryCode}

\&#x20;     })(\\\_\\\_entryMod, \\\_\\\_entryMod.exports, require);



\&#x20;     const App = \\\_\\\_entryMod.exports.default || \\\_\\\_entryMod.exports;

\&#x20;     if (App \\\&\\\& typeof App === 'function') {

\&#x20;       ReactDOM.createRoot(document.getElementById('root')).render(React.createElement(App));

\&#x20;     } else {

\&#x20;       document.getElementById('root').innerHTML = '<p style="color:red">No default export found in ' + ${JSON.stringify(entryFile)} + '</p>';

\&#x20;     }

\&#x20;   } catch(err) {

\&#x20;     document.getElementById('root').innerHTML =

\&#x20;       '<pre style="color:red;padding:1rem;font-size:12px">' + err.message + '\\\\\\\\n\\\\\\\\n' + (err.stack || '') + '</pre>';

\&#x20;   }

\&#x20; </script>

</body>

</html>`;



\&#x20; return { html, errors };

}

```



\---



\## lib/aiPipeline.js



```js

export function buildPromptContext(request) {

\&#x20; const { prompt, currentFiles = \\\[], targetFile, mode = 'edit' } = request;



\&#x20; const fileContext = (targetFile

\&#x20;   ? currentFiles.filter(f => f.path === targetFile)

\&#x20;   : currentFiles

\&#x20; ).map(f => `// FILE: ${f.path}\\\\n${f.content}`).join('\\\\n\\\\n---\\\\n\\\\n');



\&#x20; return {

\&#x20;   systemPrompt: `You are an expert React/JSX developer. Respond only with code changes in the required JSON format.`,

\&#x20;   userPrompt: `Mode: ${mode}\\\\nInstruction: ${prompt}\\\\n\\\\nCurrent files:\\\\n${fileContext}`,

\&#x20;   mode,

\&#x20;   targetFile

\&#x20; };

}



export async function callAIProvider(promptContext) {

\&#x20; // STUB — replace with actual AI call, e.g.:

\&#x20; // const result = await base44.integrations.Core.InvokeLLM({

\&#x20; //   prompt: promptContext.userPrompt,

\&#x20; //   response\\\_json\\\_schema: AI\\\_RESPONSE\\\_SCHEMA

\&#x20; // });



\&#x20; console.log('\\\[AI Pipeline] callAIProvider called (stub)', promptContext);

\&#x20; await new Promise(r => setTimeout(r, 300));



\&#x20; return {

\&#x20;   raw: null,

\&#x20;   stub: true,

\&#x20;   message: 'AI provider not yet connected. Wire in callAIProvider() in src/lib/aiPipeline.js.'

\&#x20; };

}



export function parseAIResponse(rawResponse, currentFiles) {

\&#x20; if (rawResponse.stub) {

\&#x20;   return { fileChanges: \\\[], message: rawResponse.message, error: null };

\&#x20; }



\&#x20; const data = typeof rawResponse.raw === 'string'

\&#x20;   ? JSON.parse(rawResponse.raw)

\&#x20;   : rawResponse.raw;



\&#x20; return {

\&#x20;   fileChanges: data?.changes || \\\[],

\&#x20;   message: data?.message || '',

\&#x20;   error: null

\&#x20; };

}



export function applyFileChanges(currentFiles, fileChanges) {

\&#x20; let updated = \\\[...currentFiles];



\&#x20; for (const change of fileChanges) {

\&#x20;   if (change.action === 'delete') {

\&#x20;     updated = updated.filter(f => f.path !== change.path);

\&#x20;   } else if (change.action === 'create') {

\&#x20;     updated = \\\[...updated, { path: change.path, content: change.content, language: inferLang(change.path) }];

\&#x20;   } else {

\&#x20;     const idx = updated.findIndex(f => f.path === change.path);

\&#x20;     if (idx >= 0) {

\&#x20;       updated\\\[idx] = { ...updated\\\[idx], content: change.content };

\&#x20;     } else {

\&#x20;       updated = \\\[...updated, { path: change.path, content: change.content, language: inferLang(change.path) }];

\&#x20;     }

\&#x20;   }

\&#x20; }



\&#x20; return updated;

}



export async function runAIPipeline(request) {

\&#x20; const context = buildPromptContext(request);

\&#x20; const rawResponse = await callAIProvider(context);

\&#x20; const { fileChanges, message, error } = parseAIResponse(rawResponse, request.currentFiles);



\&#x20; if (error) return { files: request.currentFiles, message, error };



\&#x20; const updatedFiles = applyFileChanges(request.currentFiles, fileChanges);

\&#x20; return { files: updatedFiles, fileChanges, message, error: null };

}



function inferLang(path) {

\&#x20; const ext = path.split('.').pop()?.toLowerCase() || '';

\&#x20; const map = { js: 'javascript', jsx: 'jsx', ts: 'typescript', tsx: 'tsx', css: 'css', html: 'html' };

\&#x20; return map\\\[ext] || 'plaintext';

}



export const AI\\\_RESPONSE\\\_SCHEMA = {

\&#x20; type: 'object',

\&#x20; properties: {

\&#x20;   message: { type: 'string' },

\&#x20;   changes: {

\&#x20;     type: 'array',

\&#x20;     items: {

\&#x20;       type: 'object',

\&#x20;       properties: {

\&#x20;         path: { type: 'string' },

\&#x20;         action: { type: 'string', enum: \\\['create', 'update', 'delete'] },

\&#x20;         content: { type: 'string' }

\&#x20;       },

\&#x20;       required: \\\['path', 'action']

\&#x20;     }

\&#x20;   }

\&#x20; },

\&#x20; required: \\\['message', 'changes']

};

```



\---



\## lib/constants.js



```js

export const DEFAULT\\\_PROJECT\\\_FILES = \\\[

\&#x20; {

\&#x20;   path: 'App.jsx',

\&#x20;   language: 'jsx',

\&#x20;   content: `import { useState } from "react";

import Sidebar from "./Sidebar.jsx";

import Dashboard from "./Dashboard.jsx";



export default function App() {

\&#x20; const \\\[activeNav, setActiveNav] = useState("Dashboard");

\&#x20; return (

\&#x20;   <div style={{ display: "flex", height: "100vh", background: "#0f0f1a", fontFamily: "'Inter', 'Segoe UI', sans-serif", overflow: "hidden" }}>

\&#x20;     <Sidebar active={activeNav} onNav={setActiveNav} />

\&#x20;     <main style={{ flex: 1, overflowY: "auto" }}>

\&#x20;       <Dashboard />

\&#x20;     </main>

\&#x20;   </div>

\&#x20; );

}`

\&#x20; },

\&#x20; // ... (Sidebar.jsx, Dashboard.jsx, StatCard.jsx, MiniChart.jsx, ActivityFeed.jsx, index.css)

\&#x20; // Full content preserved — see original constants.js for complete DEFAULT\\\_PROJECT\\\_FILES array

];



export const LANGUAGE\\\_MAP = {

\&#x20; js: 'javascript',

\&#x20; jsx: 'jsx',

\&#x20; ts: 'typescript',

\&#x20; tsx: 'tsx',

\&#x20; css: 'css',

\&#x20; html: 'html',

\&#x20; json: 'json',

\&#x20; md: 'markdown'

};



export const LOCAL\\\_STORAGE\\\_PREFIX = 'ai\\\_builder\\\_project\\\_';

export const PREVIEW\\\_DEBOUNCE\\\_MS = 600;

export const CLOUD\\\_SYNC\\\_DEBOUNCE\\\_MS = 3000;

```



\---



\## lib/fileUtils.js



```js

import { LANGUAGE\\\_MAP } from './constants';



export function getLanguageFromPath(filePath) {

\&#x20; const ext = filePath.split('.').pop()?.toLowerCase() || '';

\&#x20; return LANGUAGE\\\_MAP\\\[ext] || 'plaintext';

}



export function normalizePath(filePath) {

\&#x20; return filePath.trim().replace(/^\\\\/+/, '');

}



export function createFile(path, content = '') {

\&#x20; return {

\&#x20;   path: normalizePath(path),

\&#x20;   language: getLanguageFromPath(path),

\&#x20;   content

\&#x20; };

}



export function upsertFile(files, updatedFile) {

\&#x20; const exists = files.some(f => f.path === updatedFile.path);

\&#x20; if (exists) {

\&#x20;   return files.map(f => f.path === updatedFile.path ? { ...f, ...updatedFile } : f);

\&#x20; }

\&#x20; return \\\[...files, updatedFile];

}



export function removeFile(files, path) {

\&#x20; return files.filter(f => f.path !== path);

}



export function renameFile(files, oldPath, newPath) {

\&#x20; return files.map(f =>

\&#x20;   f.path === oldPath

\&#x20;     ? { ...f, path: normalizePath(newPath), language: getLanguageFromPath(newPath) }

\&#x20;     : f

\&#x20; );

}



export function findFile(files, path) {

\&#x20; return files.find(f => f.path === path) || null;

}

```



\---



\## lib/localCache.js



```js

import { LOCAL\\\_STORAGE\\\_PREFIX } from './constants';



const META\\\_KEY = `${LOCAL\\\_STORAGE\\\_PREFIX}projects\\\_meta`;



export function saveProjectLocally(project) {

\&#x20; const key = `${LOCAL\\\_STORAGE\\\_PREFIX}${project.id}`;

\&#x20; localStorage.setItem(key, JSON.stringify({ ...project, \\\_cached\\\_at: Date.now() }));

\&#x20; updateMeta(project.id, project.name);

}



export function loadProjectLocally(projectId) {

\&#x20; const key = `${LOCAL\\\_STORAGE\\\_PREFIX}${projectId}`;

\&#x20; const raw = localStorage.getItem(key);

\&#x20; return raw ? JSON.parse(raw) : null;

}



export function deleteProjectLocally(projectId) {

\&#x20; const key = `${LOCAL\\\_STORAGE\\\_PREFIX}${projectId}`;

\&#x20; localStorage.removeItem(key);

\&#x20; removeMeta(projectId);

}



export function listLocalProjects() {

\&#x20; const raw = localStorage.getItem(META\\\_KEY);

\&#x20; return raw ? JSON.parse(raw) : \\\[];

}



function updateMeta(id, name) {

\&#x20; const existing = listLocalProjects();

\&#x20; const filtered = existing.filter(p => p.id !== id);

\&#x20; localStorage.setItem(META\\\_KEY, JSON.stringify(\\\[...filtered, { id, name, \\\_cached\\\_at: Date.now() }]));

}



function removeMeta(id) {

\&#x20; const existing = listLocalProjects();

\&#x20; localStorage.setItem(META\\\_KEY, JSON.stringify(existing.filter(p => p.id !== id)));

}

```



\---



\## lib/previewSandbox.js



```js

export const ERROR\\\_RELAY\\\_SCRIPT = `

<script>

\&#x20; window.addEventListener('error', function(event) {

\&#x20;   window.parent.postMessage({

\&#x20;     type: 'PREVIEW\\\_RUNTIME\\\_ERROR',

\&#x20;     error: {

\&#x20;       message: event.message,

\&#x20;       stack: event.error ? event.error.stack : null,

\&#x20;       filename: event.filename,

\&#x20;       lineno: event.lineno,

\&#x20;       colno: event.colno

\&#x20;     }

\&#x20;   }, '\\\*');

\&#x20; });

\&#x20; window.addEventListener('unhandledrejection', function(event) {

\&#x20;   window.parent.postMessage({

\&#x20;     type: 'PREVIEW\\\_RUNTIME\\\_ERROR',

\&#x20;     error: {

\&#x20;       message: 'Unhandled Promise Rejection: ' + (event.reason?.message || String(event.reason)),

\&#x20;       stack: event.reason?.stack || null

\&#x20;     }

\&#x20;   }, '\\\*');

\&#x20; });

\&#x20; const \\\_origConsole = { log: console.log, warn: console.warn, error: console.error };

\&#x20; \\\['log', 'warn', 'error'].forEach(function(level) {

\&#x20;   console\\\[level] = function() {

\&#x20;     var args = Array.from(arguments).map(function(a) {

\&#x20;       try { return typeof a === 'object' ? JSON.stringify(a) : String(a); } catch(e) { return String(a); }

\&#x20;     });

\&#x20;     window.parent.postMessage({ type: 'PREVIEW\\\_CONSOLE', level: level, args: args }, '\\\*');

\&#x20;     \\\_origConsole\\\[level].apply(console, arguments);

\&#x20;   };

\&#x20; });

<\\\\/script>

`;



export function injectErrorRelay(html) {

\&#x20; if (html.includes('</body>')) {

\&#x20;   return html.replace('</body>', `${ERROR\\\_RELAY\\\_SCRIPT}</body>`);

\&#x20; }

\&#x20; return html + ERROR\\\_RELAY\\\_SCRIPT;

}



export function getSandboxAttributes() {

\&#x20; return \\\[

\&#x20;   'allow-scripts',

\&#x20;   'allow-same-origin',

\&#x20;   'allow-forms',

\&#x20;   'allow-modals'

\&#x20; ].join(' ');

}



export function createPreviewBlobURL(html) {

\&#x20; const blob = new Blob(\\\[html], { type: 'text/html' });

\&#x20; return URL.createObjectURL(blob);

}

```



\---

[base 444](base%2520444)

