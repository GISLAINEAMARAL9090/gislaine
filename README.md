import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

const products = [
  { id: 1, name: "Produto 1", price: 50 },
  { id: 2, name: "Produto 2", price: 80 },
  { id: 3, name: "Produto 3", price: 100 },
];

export default function Shop() {
  const [cart, setCart] = useState([]);

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  return (
    <div className="p-6">
      <h1 className="text-2xl font-bold mb-4">Loja Virtual</h1>
      <div className="grid grid-cols-3 gap-4">
        {products.map((product) => (
          <Card key={product.id} className="p-4">
            <CardContent>
              <h2 className="text-lg font-semibold">{product.name}</h2>
              <p className="text-gray-600">R$ {product.price}</p>
              <Button className="mt-2" onClick={() => addToCart(product)}>
                Adicionar ao Carrinho
              </Button>
            </CardContent>
          </Card>
        ))}
      </div>
      <div className="mt-6 p-4 border rounded-lg">
        <h2 className="text-xl font-bold">Carrinho</h2>
        {cart.length === 0 ? (
          <p className="text-gray-500">O carrinho está vazio</p>
        ) : (
          cart.map((item, index) => (
            <p key={index} className="text-gray-700">{item.name} - R$ {item.price}</p>
          ))
        )}
        <Button className="mt-4">Finalizar Compra</Button>
      </div>
    </div>
  );
}
