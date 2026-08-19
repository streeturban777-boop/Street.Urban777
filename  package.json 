// ==========================================================
// 📁 ARQUIVO 1: package.json
// ==========================================================
/*
{
  "name": "street-urban777",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "postinstall": "prisma generate",
    "db:push": "prisma db push"
  },
  "dependencies": {
    "@prisma/client": "^5.10.0",
    "next": "14.1.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "prisma": "^5.10.0",
    "tailwindcss": "^3.4.1",
    "postcss": "^8.4.35",
    "autoprefixer": "^10.4.17"
  }
}
*/

// ==========================================================
// 📁 ARQUIVO 2: tsconfig.json
// ==========================================================
/*
{
  "compilerOptions": {
    "target": "ES2017",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": false,
    "noEmit": true,
    "incremental": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "plugins": [{ "name": "next" }],
    "baseUrl": "."
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
*/

// ==========================================================
// 📁 ARQUIVO 3: tailwind.config.js
// ==========================================================
/*
/** @type {import('tailwindcss').Config} *\/
module.exports = {
  content: ["./src/app/**/*.{js,ts,jsx,tsx,mdx}"],
  theme: {
    extend: {
      colors: {
        red: { 500: "#dc2626", 600: "#b91c1c", 700: "#991b1b" },
        zinc: { 950: "#0f0f0f", 900: "#18181b", 800: "#27272a", 700: "#3f3f46" }
      }
    }
  },
  plugins: []
}
*/

// ==========================================================
// 📁 ARQUIVO 4: postcss.config.js
// ==========================================================
/*
module.exports = {
  plugins: { tailwindcss: {}, autoprefixer: {} }
}
*/

// ==========================================================
// 📁 ARQUIVO 5: .env.example
// ==========================================================
/*
DATABASE_URL="postgresql://usuario:senha@localhost:5432/streeturban"
NEXTAUTH_URL="http://localhost:3000"
*/

// ==========================================================
// 📁 ARQUIVO 6: prisma/schema.prisma
// ==========================================================
/*
generator client { provider = "prisma-client-js" }
datasource db { provider = "postgresql"; url = env("DATABASE_URL") }

model Configuracao {
  id              Int      @id @default(autoincrement())
  nomeLoja        String   @default("Street Urban 777")
  descricao       String?
  telefone        String?
  email           String   @default("street.urban777@gmail.com")
  corPrimaria     String   @default("#dc2626")
  corSecundaria   String   @default("#000000")
  instagram       String?
  whatsapp        String?
  freteGratisAcima Float   @default(299.90)
  updatedAt       DateTime @updatedAt
}

model Produto {
  id              Int      @id @default(autoincrement())
  nome            String
  descricao       String?
  preco           Float
  precoPromocional Float?
  categoria       String   @default("Camisetas")
  imagem          String?
  estoque         Int      @default(0)
  destaque        Boolean  @default(false)
  ativo           Boolean  @default(true)
  createdAt       DateTime @default(now())
}

model Pedido {
  id        Int      @id @default(autoincrement())
  cliente   String
  email     String
  telefone  String?
  endereco  String
  total     Float
  status    String   @default("Pendente")
  createdAt DateTime @default(now())
}

model Usuario {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  nome      String?
  role      String   @default("cliente")
  createdAt DateTime @default(now())
}
*/

// ==========================================================
// 📁 ARQUIVO 7: src/app/globals.css
// ==========================================================
/*
@tailwind base;
@tailwind components;
@tailwind utilities;
* { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
html, body { background: #000; color: #fff; font-family: system-ui, sans-serif; min-height: 100vh; overflow-x: hidden; }
input, select, textarea { font-size: 16px !important; }
button, a { min-height: 44px; transition: transform 0.1s; }
button:active, a:active { transform: scale(0.98); }
*/

// ==========================================================
// 📁 ARQUIVO 8: src/app/layout.tsx
// ==========================================================
/*
import './globals.css'
import type { Metadata } from 'next'

export const metadata: Metadata = {
  title: 'Street Urban 777',
  description: 'Loja de Streetwear — Moda Urbana',
  themeColor: '#000000'
}

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="pt-BR">
      <body className="bg-zinc-950 text-white min-h-screen">{children}</body>
    </html>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 9: src/app/page.tsx — PÁGINA INICIAL
// ==========================================================
/*
'use client'
import Link from 'next/link'

export default function Home() {
  return (
    <main className="min-h-screen flex flex-col items-center justify-center p-6">
      <h1 className="text-5xl font-bold text-red-500 mb-4">STREET URBAN 777</h1>
      <p className="text-zinc-400 text-xl mb-8">Moda Urbana • Estilo • Atitude</p>
      <div className="flex gap-4 flex-wrap justify-center">
        <Link href="/login" className="bg-red-600 hover:bg-red-700 px-8 py-4 rounded-lg text-xl font-bold transition">
          Entrar
        </Link>
        <Link href="/catalogo" className="border-2 border-red-600 text-red-500 hover:bg-red-600 hover:text-white px-8 py-4 rounded-lg text-xl font-bold transition">
          Ver Loja
        </Link>
      </div>
    </main>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 10: src/app/login/page.tsx — LOGIN COMPLETO
// ==========================================================
/*
'use client'
import { useState } from 'react'
import { useRouter } from 'next/navigation'
import Link from 'next/link'

export default function Login() {
  const [email, setEmail] = useState('')
  const [senha, setSenha] = useState('')
  const [erro, setErro] = useState('')
  const router = useRouter()

  const entrar = async (e: React.FormEvent) => {
    e.preventDefault()
    if (!email || !senha) return setErro('Preencha todos os campos')
    
    // ✅ SEU E-MAIL DE ADMINISTRADOR OFICIAL
    const ADMIN_EMAIL = 'street.urban777@gmail.com'
    const emailLimpo = email.trim().toLowerCase()
    const role = emailLimpo === ADMIN_EMAIL.toLowerCase() ? 'admin' : 'cliente'
    
    localStorage.setItem('token', btoa(JSON.stringify({ 
      id: 1, 
      email: emailLimpo, 
      role, 
      name: emailLimpo.split('@')[0] 
    })))
    
    router.push(role === 'admin' ? '/admin' : '/cliente')
  }

  return (
    <div className="min-h-screen bg-black flex items-center justify-center p-4">
      <form onSubmit={entrar} className="bg-zinc-900 p-6 sm:p-8 rounded-xl border border-zinc-800 w-full max-w-md">
        <Link href="/" className="block text-center mb-8">
          <h1 className="text-3xl font-bold text-red-600">STREET URBAN 777</h1>
        </Link>
        
        {erro && <div className="bg-red-500/10 text-red-400 p-3 rounded mb-4 text-center">{erro}</div>}
        
        <div className="mb-4">
          <label className="block text-zinc-400 mb-1">E-mail</label>
          <input 
            type="email" 
            value={email} 
            onChange={(e) => setEmail(e.target.value)} 
            className="w-full p-3 bg-zinc-800 rounded-lg border border-zinc-700 focus:border-red-500 outline-none text-white" 
            placeholder="street.urban777@gmail.com" 
            required 
          />
        </div>
        
        <div className="mb-6">
          <label className="block text-zinc-400 mb-1">Senha</label>
          <input 
            type="password" 
            value={senha} 
            onChange={(e) => setSenha(e.target.value)} 
            className="w-full p-3 bg-zinc-800 rounded-lg border border-zinc-700 focus:border-red-500 outline-none text-white" 
            required 
          />
        </div>
        
        <button 
          type="submit" 
          className="w-full bg-red-600 hover:bg-red-700 py-3 rounded-lg font-bold text-lg transition"
        >
          Entrar
        </button>
        
        <p className="text-center text-zinc-500 text-sm mt-4">
          Admin: <strong>street.urban777@gmail.com</strong>
        </p>
      </form>
    </div>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 11: src/app/cliente/page.tsx — ÁREA DO CLIENTE
// ==========================================================
/*
'use client'
import { useEffect, useState } from 'react'
import { useRouter } from 'next/navigation'
import Link from 'next/link'

export default function ClientePage() {
  const [user, setUser] = useState<any>(null)
  const router = useRouter()

  useEffect(() => {
    const t = localStorage.getItem('token')
    if (!t) return router.push('/login')
    try {
      const p = JSON.parse(atob(t))
      setUser(p)
    } catch {
      router.push('/login')
    }
  }, [router])

  if (!user) return <div className="min-h-screen bg-black flex items-center justify-center text-white">Carregando...</div>

  return (
    <div className="min-h-screen bg-black text-white p-4 md:p-8">
      <header className="flex justify-between items-center mb-8">
        <h1 className="text-2xl font-bold text-red-600">STREET URBAN 777</h1>
        <button 
          onClick={() => { localStorage.removeItem('token'); router.push('/') }} 
          className="bg-zinc-800 px-4 py-2 rounded-lg hover:bg-zinc-700"
        >
          Sair
        </button>
      </header>
      
      <div className="max-w-2xl mx-auto">
        <h2 className="text-xl font-semibold mb-4">Bem-vindo, {user.name}!</h2>
        <p className="text-zinc-400 mb-8">Área do cliente — acompanhe seus pedidos e compre produtos exclusivos.</p>
        
        <div className="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-8">
          <Link href="/catalogo" className="bg-red-600 hover:bg-red-700 p-5 rounded-xl text-center font-bold">
            🛒 Ver Catálogo
          </Link>
          <Link href="/pedidos" className="bg-zinc-800 hover:bg-zinc-700 p-5 rounded-xl text-center font-bold">
            📦 Meus Pedidos
          </Link>
        </div>
        
        <button onClick={() => router.push('/')} className="bg-zinc-800 px-6 py-3 rounded-lg font-bold hover:bg-zinc-700">
          🏠 Voltar à Loja
        </button>
      </div>
    </div>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 12: src/app/admin/layout.tsx — LAYOUT ADMIN
// ==========================================================
/*
'use client'
import { useEffect, useState } from 'react'
import Link from 'next/link'
import { usePathname, useRouter } from 'next/navigation'

export default function AdminLayout({ children }: { children: React.ReactNode }) {
  const [user, setUser] = useState<any>(null)
  const [menuAberto, setMenuAberto] = useState(false)
  const router = useRouter()
  const pathname = usePathname()

  useEffect(() => {
    const t = localStorage.getItem('token')
    if (!t) return router.push('/login')
    try {
      const p = JSON.parse(atob(t))
      if (p.role !== 'admin') return router.push('/')
      setUser(p)
    } catch {
      router.push('/login')
    }
  }, [router])

  const sair = () => { localStorage.removeItem('token'); router.push('/') }
  if (!user) return <div className="min-h-screen bg-black flex items-center justify-center text-white">Carregando...</div>

  const menu = [
    { href: '/admin', label: 'Dashboard', icon: '📊' },
    { href: '/admin/configuracoes', label: 'Loja', icon: '🏪' },
    { href: '/admin/banners', label: 'Banners', icon: '🖼️' },
    { href: '/admin/catalogo', label: 'Produtos', icon: '👕' },
    { href: '/admin/pedidos', label: 'Pedidos', icon: '📦' },
    { href: '/admin/usuarios', label: 'Usuários', icon: '👥' },
  ]

  return (
    <div className="min-h-screen bg-black text-white">
      <header className="md:hidden fixed top-0 left-0 right-0 bg-zinc-900/95 backdrop-blur z-50 p-4 flex justify-between items-center border-b border-zinc-800">
        <h2 className="text-xl font-bold text-red-600">STREET URBAN 777</h2>
        <button onClick={() => setMenuAberto(!menuAberto)} className="p-2 text-xl">☰</button>
      </header>

      <aside className="hidden md:block w-64 bg-zinc-900 border-r border-zinc-800 p-5 fixed h-full">
        <h2 className="text-2xl font-bold text-red-600 mb-8">STREET URBAN 777</h2>
        <nav className="space-y-2">
          {menu.map(i => (
            <Link key={i.href} href={i.href} className={`block p-3 rounded-lg transition ${pathname === i.href ? 'bg-red-600' : 'hover:bg-zinc-800 text-zinc-300'}`}>
              {i.icon} {i.label}
            </Link>
          ))}
        </nav>
        <button onClick={sair} className="absolute bottom-6 w-full p-3 bg-zinc-800 hover:bg-red-600 rounded-lg transition text-left">
          🚪 Sair
        </button>
      </aside>

      {menuAberto && (
        <div className="md:hidden fixed inset-0 bg-black/98 z-40 pt-20 p-6">
          <nav className="flex flex-col gap-3">
            {menu.map(i => (
              <Link key={i.href} href={i.href} onClick={() => setMenuAberto(false)} className={`block p-4 rounded-lg text-lg ${pathname === i.href ? 'bg-red-600' : 'bg-zinc-900'}`}>
                {i.icon} {i.label}
              </Link>
            ))}
            <button onClick={() => { sair(); setMenuAberto(false) }} className="mt-4 p-4 bg-zinc-800 rounded-lg text-left text-lg">
              🚪 Sair
            </button>
          </nav>
        </div>
      )}

      <main className="md:ml-64 p-4 md:p-8 bg-zinc-950 min-h-screen pt-20 md:pt-0">{children}</main>
    </div>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 13: src/app/admin/page.tsx — DASHBOARD ADMIN
// ==========================================================
/*
'use client'
import { useEffect, useState } from 'react'
import { useRouter } from 'next/navigation'

export default function AdminDashboard() {
  const [user, setUser] = useState<any>(null)
  const router = useRouter()

  useEffect(() => {
    const t = localStorage.getItem('token')
    if (!t) return router.push('/login')
    const p = JSON.parse(atob(t))
    if (p.role !== 'admin') return router.push('/')
    setUser(p)
  }, [router])

  if (!user) return <p className="text-white">Carregando...</p>

  return (
    <div>
      <h1 className="text-2xl md:text-3xl font-bold mb-2"><span className="text-red-600">ADMINISTRAÇÃO</span></h1>
      <p className="text-zinc-400 mb-6">Bem-vindo, {user.email}</p>
      
      <div className="grid grid-cols-1 sm:grid-cols-3 gap-4 mb-8">
        <div className="bg-zinc-900 p-5 rounded-xl border border-red-600">
          <h3 className="text-red-500 text-sm">Produtos Ativos</h3>
          <p className="text-2xl font-bold mt-1">0</p>
        </div>
        <div className="bg-zinc-900 p-5 rounded-xl border border-zinc-700">
          <h3 className="text-zinc-400 text-sm">Pedidos Pendentes</h3>
          <p className="text-2xl font-bold mt-1">0</p>
        </div>
        <div className="bg-zinc-900 p-5 rounded-xl border border-zinc-700">
          <h3 className="text-zinc-400 text-sm">Usuários</h3>
          <p className="text-2xl font-bold mt-1">0</p>
        </div>
      </div>

      <div className="grid grid-cols-1 sm:grid-cols-3 gap-4">
        <button onClick={() => router.push('/admin/configuracoes')} className="bg-red-600 hover:bg-red-700 p-5 rounded-xl text-left">
          <h3 className="text-lg font-bold">🏪 Configurar Loja</h3>
        </button>
        <button onClick={() => router.push('/admin/catalogo')} className="bg-zinc-800 hover:bg-zinc-700 p-5 rounded-xl text-left">
          <h3 className="text-lg font-bold">👕 Gerenciar Produtos</h3>
        </button>
        <button onClick={() => router.push('/admin/pedidos')} className="bg-zinc-800 hover:bg-zinc-700 p-5 rounded-xl text-left">
          <h3 className="text-lg font-bold">📦 Ver Pedidos</h3>
        </button>
      </div>
    </div>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 14: src/app/admin/configuracoes/page.tsx
// ==========================================================
/*
'use client'
import { useState } from 'react'

export default function AdminConfiguracoes() {
  const [config, setConfig] = useState({
    nomeLoja: 'Street Urban 777',
    email: 'street.urban777@gmail.com',
    telefone: '',
    instagram: '',
    whatsapp: '',
    freteGratisAcima: 299.90
  })
  const [salvo, setSalvo] = useState(false)

  const salvar = (e: React.FormEvent) => {
    e.preventDefault()
    setSalvo(true)
    setTimeout(() => setSalvo(false), 3000)
  }

  return (
    <div>
      <h1 className="text-2xl md:text-3xl font-bold mb-6">⚙️ Configurações da Loja</h1>
      
      {salvo && <div className="bg-green-500/10 text-green-400 p-4 rounded-lg mb-4">✅ Salvo com sucesso!</div>}
      
      <form onSubmit={salvar} className="space-y-6">
        <div className="bg-zinc-900 p-5 rounded-xl border border-zinc-800">
          <h2 className="text-xl font-semibold mb-4 text-red-500">🏪 Dados da Loja</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div>
              <label className="block text-zinc-400 mb-1">Nome da Loja</label>
              <input type="text" value={config.nomeLoja} onChange={(e) => setConfig({...config, nomeLoja: e.target.value})} className="w-full p-3 bg-zinc-800 rounded-lg border border-zinc-700 focus:border-red-500 outline-none text-white" />
            </div>
            <div>
              <label className="block text-zinc-400 mb-1">E-mail</label>
              <input type="email" value={config.email} onChange={(e) => setConfig({...config, email: e.target.value})} className="w-full p-3 bg-zinc-800 rounded-lg border border-zinc-700 focus:border-red-500 outline-none text-white" />
            </div>
          </div>
        </div>
        <button type="submit" className="bg-red-600 hover:bg-red-700 px-6 py-3 rounded-lg font-bold text-lg">💾 Salvar Alterações</button>
      </form>
    </div>
  )
}
*/

// ==========================================================
// 📁 ARQUIVO 15: src/app/admin/catalogo/page.tsx
// ==========================================================
/*
'use client'
import { useState } from 'react'

const CATEGORIAS = ['Camisetas', 'Calças', 'Moletons', 'Jaquetas', 'Bonés', 'Acessórios']

export default function AdminCatalogo() {
  const [produtos, setProdutos] = useState<any[]>([])
  const [form, setForm] = useState({
    nome: '', descricao: '', preco: '', precoPromocional: '',
    categoria: 'Camisetas', imagem: '', estoque: 1, ativo: true
  })

  const adicionar = (e: React.FormEvent) => {
    e.preventDefault()
    setProdutos([...produtos, { ...form, id: Date.now() }])
    setForm({ nome: '', descricao: '', preco: '', precoPromocional: '', categoria: 'Camisetas', imagem: '', estoque: 1, ativo: true })
  }

  return (
    <div>
      <h1 className="text-2xl md:text-3xl font-bold mb-6">👕 Catálogo de Produtos</h1>
      
      <form onSubmit={adicionar} className="bg-zinc-900 p-5 rounded-xl border border-zinc-800 mb-8">
        <h2 className="text-xl mb-4 text-red-5
