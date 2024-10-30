import React, { useState } from 'react';
import { Play, Pause, ShoppingCart, Star, Download, Search, User, Menu, X, Home, Music, Heart, Settings } from 'lucide-react';
import { Card, CardHeader, CardTitle, CardContent } from '@/components/ui/card';

const MusicMarketplace = () => {
  const [playing, setPlaying] = useState(null);
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);

  const beats = [
    {
      id: 1,
      title: "Summer Groove",
      producer: "Beat Master Juan",
      genre: "Hip-Hop",
      price: "₱1,500",
      rating: 4.5,
      image: "/api/placeholder/300/200"
    },
    {
      id: 2,
      title: "Manila Nights",
      producer: "Producer Carlo",
      genre: "R&B",
      price: "₱2,000",
      rating: 5.0,
      image: "/api/placeholder/300/200"
    },
    {
      id: 3,
      title: "Island Vibes",
      producer: "DJ Maria",
      genre: "Pop",
      price: "₱1,800",
      rating: 4.8,
      image: "/api/placeholder/300/200"
    }
  ];

  const featuredSongs = [
    {
      id: 1,
      title: "Ikaw Lang",
      artist: "Sarah Santos",
      plays: "50K",
      image: "/api/placeholder/300/200"
    },
    {
      id: 2,
      title: "Mahal Kita",
      artist: "Mike Dela Cruz",
      plays: "30K",
      image: "/api/placeholder/300/200"
    }
  ];

  return (
    <div className="min-h-screen relative bg-gradient-to-br from-purple-900 via-blue-900 to-black">
      {/* Animated background effects */}
      <div className="absolute inset-0 overflow-hidden">
        <div className="absolute w-full h-full bg-[radial-gradient(circle_at_50%_50%,rgba(76,29,149,0.3),rgba(30,58,138,0.1))] animate-pulse"></div>
        <div className="absolute top-0 left-0 w-full h-full opacity-30">
          <div className="absolute top-1/4 left-1/4 w-32 h-32 bg-blue-500 rounded-full filter blur-3xl"></div>
          <div className="absolute top-1/3 right-1/3 w-32 h-32 bg-purple-500 rounded-full filter blur-3xl"></div>
          <div className="absolute bottom-1/4 right-1/4 w-32 h-32 bg-pink-500 rounded-full filter blur-3xl"></div>
        </div>
      </div>

      {/* Header */}
      <header className="relative z-20 backdrop-blur-lg bg-black/40 border-b border-white/10">
        <nav className="container mx-auto px-6 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center space-x-2">
              <Music className="text-purple-400 h-8 w-8" />
              <span className="text-2xl font-bold text-white">PinoyBeats</span>
            </div>

            <div className="hidden md:flex items-center space-x-8">
              <a href="#" className="text-white hover:text-purple-400 transition-colors">Home</a>
              <a href="#" className="text-white hover:text-purple-400 transition-colors">Beats</a>
              <a href="#" className="text-white hover:text-purple-400 transition-colors">Artists</a>
              <a href="#" className="text-white hover:text-purple-400 transition-colors">Pricing</a>
              <div className="relative">
                <Search className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400 h-5 w-5" />
                <input
                  type="text"
                  placeholder="Search beats..."
                  className="bg-white/10 border border-white/20 rounded-full py-2 pl-10 pr-4 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-purple-500"
                />
              </div>
            </div>

            <div className="hidden md:flex items-center space-x-4">
              <button className="text-white hover:text-purple-400">
                <ShoppingCart className="h-6 w-6" />
              </button>
              <button className="bg-gradient-to-r from-purple-500 to-blue-500 text-white px-4 py-2 rounded-full hover:from-purple-600 hover:to-blue-600 transition-all duration-300">
                Sign In
              </button>
            </div>

            <button 
              className="md:hidden text-white"
              onClick={() => setMobileMenuOpen(!mobileMenuOpen)}
            >
              {mobileMenuOpen ? <X className="h-6 w-6" /> : <Menu className="h-6 w-6" />}
            </button>
          </div>

          {mobileMenuOpen && (
            <div className="md:hidden absolute top-full left-0 w-full backdrop-blur-lg bg-black/90 border-b border-white/10">
              <div className="px-4 py-2 space-y-4">
                <a href="#" className="block text-white hover:text-purple-400 py-2">Home</a>
                <a href="#" className="block text-white hover:text-purple-400 py-2">Beats</a>
                <a href="#" className="block text-white hover:text-purple-400 py-2">Artists</a>
                <a href="#" className="block text-white hover:text-purple-400 py-2">Pricing</a>
                <div className="relative">
                  <Search className="absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400 h-5 w-5" />
                  <input
                    type="text"
                    placeholder="Search beats..."
                    className="w-full bg-white/10 border border-white/20 rounded-full py-2 pl-10 pr-4 text-white placeholder-gray-400"
                  />
                </div>
              </div>
            </div>
          )}
        </nav>
      </header>

      {/* Main Content */}
      <main className="relative z-10 container mx-auto px-6 py-8">
        {/* Featured Beats */}
        <h2 className="text-2xl font-bold mb-4 text-white">Featured Beats</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-8">
          {beats.map((beat) => (
            <Card key={beat.id} className="backdrop-blur-lg bg-white/10 border border-white/20 text-white hover:bg-white/20 transition-all duration-300">
              <img src={beat.image} alt={beat.title} className="w-full h-48 object-cover rounded-t-lg"/>
              <CardContent className="p-4">
                <div className="flex justify-between items-center mb-2">
                  <h3 className="text-lg font-bold">{beat.title}</h3>
                  <button 
                    className="p-2 bg-blue-500 hover:bg-blue-600 text-white rounded-full transition-colors duration-300"
                    onClick={() => setPlaying(playing === beat.id ? null : beat.id)}
                  >
                    {playing === beat.id ? <Pause size={20} /> : <Play size={20} />}
                  </button>
                </div>
                <p className="text-gray-300 mb-2">{beat.producer}</p>
                <div className="flex justify-between items-center">
                  <span className="bg-white/20 px-2 py-1 rounded text-sm">{beat.genre}</span>
                  <div className="flex items-center">
                    <Star className="text-yellow-400 mr-1" size={16} />
                    <span>{beat.rating}</span>
                  </div>
                </div>
                <div className="mt-4 flex justify-between items-center">
                  <span className="font-bold text-lg">{beat.price}</span>
                  <button className="bg-gradient-to-r from-blue-500 to-purple-500 text-white px-4 py-2 rounded hover:from-blue-600 hover:to-purple-600 transition-all duration-300">
                    Bumili
                  </button>
                </div>
              </CardContent>
            </Card>
          ))}
        </div>

        {/* Featured Songs */}
        <h2 className="text-2xl font-bold mb-4 text-white">Featured Songs</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
          {featuredSongs.map((song) => (
            <Card key={song.id} className="backdrop-blur-lg bg-white/10 border border-white/20 text-white hover:bg-white/20 transition-all duration-300">
              <div className="flex">
                <img src={song.image} alt={song.title} className="w-32 h-32 object-cover rounded-l-lg"/>
                <CardContent className="p-4 flex-1">
                  <h3 className="text-lg font-bold mb-1">{song.title}</h3>
                  <p className="text-gray-300 mb-2">{song.artist}</p>
                  <div className="flex items-center text-gray-300">
                    <Play size={16} className="mr-1" />
                    <span>{song.plays} plays</span>
                  </div>
                  <button className="mt-4 bg-gradient-to-r from-green-500 to-teal-500 text-white px-4 py-2 rounded hover:from-green-600 hover:to-teal-600 transition-all duration-300">
                    I-promote
                  </button>
                </CardContent>
              </div>
            </Card>
          ))}
        </div>
      </main>

      {/* Footer */}
      <footer className="relative z-20 backdrop-blur-lg bg-black/40 border-t border-white/10 text-white mt-12">
        <div className="container mx-auto px-6 py-12">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
            <div className="space-y-4">
              <div className="flex items-center space-x-2">
                <Music className="text-purple-400 h-6 w-6" />
                <span className="text-xl font-bold">PinoyBeats</span>
              </div>
              <p className="text-gray-400">Ang #1 marketplace para sa Pinoy music producers at artists.</p>
              <div className="flex space-x-4">
                <a href="#" className="text-white hover:text-purple-400">FB</a>
                <a href="#" className="text-white hover:text-purple-400">TW</a>
                <a href="#" className="text-white hover:text-purple-400">IG</a>
              </div>
            </div>

            <div>
              <h3 className="text-lg font-bold mb-4">Quick Links</h3>
              <ul className="space-y-2">
                <li><a href="#" className="text-gray-400 hover:text-purple-400">About Us</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">How It Works</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Pricing</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Blog</a></li>
              </ul>
            </div>

            <div>
              <h3 className="text-lg font-bold mb-4">Support</h3>
              <ul className="space-y-2">
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Help Center</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Terms of Service</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Privacy Policy</a></li>
                <li><a href="#" className="text-gray-400 hover:text-purple-400">Contact Us</a></li>
              </ul>
            </div>

            <div>
              <h3 className="text-lg font-bold mb-4">Stay Updated</h3>
              <p className="text-gray-400 mb-4">Subscribe sa aming newsletter para sa latest updates at promos.</p>
              <div className="flex space-x-2">
                <input
                  type="email"
                  placeholder="Enter your email"
                  className="flex-1 bg-white/10 border border-white/20 rounded-full px-4 py-2 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-purple-500"
                />
                <button className="bg-gradient-to-r from-purple-500 to-blue-500 text-white px-4 py-2 rounded-full hover:from-purple-600 hover:to-blue-600 transition-all duration-300">
                  Subscribe
                </button>
              </div>
            </div>
          </div>
          
          <div className="mt-8 pt-8 border-t border-white/10 text-center text-gray-400">
            <p>&copy; 2024 J-Lhutz Music. All rights reserved.</p>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default MusicMarketplace;

