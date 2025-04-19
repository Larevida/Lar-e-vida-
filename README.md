# Lar-e-vida-
Loja de utensílios domésticos 
// Projeto: Lar & Vida - Loja Online
// Framework: Next.js + React + Tailwind CSS

// Estrutura do projeto:
// - Home com lista de produtos
// - Painel admin para cadastrar/editar/excluir
// - Checkout com Mercado Pago e frete
// - Comentários de clientes

// Abaixo segue o código inicial para pages/index.tsx

import Head from 'next/head';
import { useEffect, useState } from 'react';

interface Produto {
  id: number;
  nome: string;
  preco: number;
  imagem: string;
}

export default function Home() {
  const [produtos, setProdutos] = useState<Produto[]>([]);

  useEffect(() => {
    // Dados simulados
    setProdutos([
      {
        id: 1,
        nome: 'Jogo de Panelas Antiaderente',
        preco: 199.99,
        imagem: '/panela.jpg',
      },
      {
        id: 2,
        nome: 'Toalha de Banho Premium',
        preco: 39.99,
        imagem: '/toalha.jpg',
      },
      {
        id: 3,
        nome: 'Lençol Casal 200 Fios',
        preco: 89.90,
        imagem: '/lencol.jpg',
      },
    ]);
  }, []);

  return (
    <div>
      <Head>
        <title>Lar & Vida</title>
      </Head>
      <header className="bg-green-600 text-white p-4 text-center text-2xl font-bold">
        Lar & Vida
      </header>
      <main className="grid grid-cols-1 md:grid-cols-3 gap-4 p-4">
        {produtos.map((produto) => (
          <div
            key={produto.id}
            className="border rounded-2xl shadow-lg p-4 flex flex-col items-center bg-white"
          >
            <img src={produto.imagem} alt={produto.nome} className="w-40 h-40 object-cover rounded-xl mb-4" />
            <h2 className="text-xl font-semibold mb-2">{produto.nome}</h2>
            <p className="text-green-700 font-bold mb-4">R$ {produto.preco.toFixed(2)}</p>
            <button className="bg-orange-500 text-white px-4 py-2 rounded-xl hover:bg-orange-600">
              Comprar
            </button>
          </div>
        ))}
      </main>
      <footer className="bg-white text-center text-sm text-gray-500 p-4 mt-4">
        &copy; 2025 Lar & Vida - Todos os direitos reservados
      </footer>
    </div>
  );
}
