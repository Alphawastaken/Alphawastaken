import React, { useState, useEffect } from 'react';
import { createRoot } from 'react-dom/client';

// The main App component that renders the interactive profile page.
const App = () => {
  // State for the animated typing effect in the header.
  const [typedText, setTypedText] = useState('');
  const [textIndex, setTextIndex] = useState(0);
  const [isTyping, setIsTyping] = useState(true);
  const fullText = "Hello, I'm Alpha!";

  // State to manage the visibility of the interactive tooltip for the tech icons.
  const [hoveredTech, setHoveredTech] = useState(null);

  // State to manage the hover effect on the "Connect" button.
  const [isConnectHovered, setIsConnectHovered] = useState(false);

  // useEffect hook to handle the typing animation.
  useEffect(() => {
    // Return early if the text is fully typed and we are no longer typing.
    if (!isTyping) return;

    // Set a timer to add a new character to the typed text.
    const typingTimer = setTimeout(() => {
      if (textIndex < fullText.length) {
        setTypedText(fullText.substring(0, textIndex + 1));
        setTextIndex(textIndex + 1);
      } else {
        // When typing is complete, stop the animation.
        setIsTyping(false);
      }
    }, 100); // Typing speed

    // Cleanup function to clear the timer when the component unmounts or re-renders.
    return () => clearTimeout(typingTimer);
  }, [textIndex, isTyping, fullText]);

  // Data for the tech toolbox to make it easy to add or remove items.
  const techStack = [
    { name: "C", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg", description: "Low-level & systems programming" },
    { name: "Python", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg", description: "Scripting and ML exploration" },
    { name: "PostgreSQL", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original-wordmark.svg", description: "Relational database management" },
    { name: "MongoDB", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original-wordmark.svg", description: "NoSQL document database" },
    { name: "Git", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg", description: "Version control" },
    { name: "Linux", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg", description: "Terminal life" },
    { name: "Azure", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/azure/azure-original.svg", description: "Cloud computing services" },
  ];

  // Data for the social links.
  const socialLinks = [
    { name: "Profile views", icon: "https://komarev.com/ghpvc/?username=alphawastaken&style=flat-square&color=blue", url: "https://github.com/alphawastaken" },
    { name: "Email", icon: "https://img.shields.io/badge/Email-Me-informational?style=flat-square&logo=gmail", url: "mailto:youremail@example.com" },
    { name: "LinkedIn", icon: "https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin", url: "https://linkedin.com/in/YOUR_USERNAME" },
  ];

  return (
    // Main container with a modern, clean design.
    <div className="min-h-screen bg-gray-100 dark:bg-gray-900 text-gray-800 dark:text-gray-200 p-4 sm:p-8 font-sans transition-colors duration-500">
      <div className="max-w-4xl mx-auto bg-white dark:bg-gray-800 rounded-3xl shadow-2xl overflow-hidden transform hover:scale-[1.005] transition-transform duration-300">
        
        {/* Header section with an animated gradient background */}
        <div className="relative p-8 sm:p-12 text-center bg-gradient-to-r from-cyan-500 to-blue-500 text-white rounded-t-3xl overflow-hidden">
          {/* Animated gradient waves for a dynamic look */}
          <div className="absolute inset-x-0 bottom-0 h-1/2 bg-white bg-opacity-10 rounded-b-3xl blur-3xl animate-pulse-slow"></div>
          <div className="relative z-10">
            <h1 className="text-4xl sm:text-5xl lg:text-6xl font-extrabold mb-2 font-inter">
              {typedText}
              <span className="inline-block w-1.5 h-8 sm:h-10 lg:h-12 ml-1 -mb-1 bg-white animate-blink"></span>
            </h1>
            <p className="text-sm sm:text-lg opacity-80 font-light tracking-wide">
              Crafting Code with C, Python, and Coffee
            </p>
          </div>
        </div>

        {/* Social links section with a smooth layout */}
        <div className="p-4 sm:p-6 flex flex-wrap justify-center gap-4">
          {socialLinks.map((link, index) => (
            <a key={index} href={link.url} target="_blank" rel="noopener noreferrer" className="transition-all duration-300 hover:scale-105">
              <img src={link.icon} alt={link.name} className="h-8" />
            </a>
          ))}
        </div>

        {/* Main content area */}
        <div className="p-6 sm:p-10 space-y-12">
          
          {/* About Me section */}
          <section className="bg-gray-50 dark:bg-gray-700 p-6 rounded-2xl shadow-inner transition-colors duration-500">
            <h3 className="text-2xl font-bold mb-4 flex items-center gap-2">
              <span role="img" aria-label="brain-emoji">🧠</span> About Me
            </h3>
            <p className="mb-4 leading-relaxed">
              🎓 I'm an undergrad at <strong className="text-blue-500">University of Athens</strong>, hacking away at:
            </p>
            <ul className="list-none space-y-2 pl-0">
              <li className="flex items-center gap-2"><span className="text-xl">🔧</span> Low-level & systems programming in <strong className="text-gray-900 dark:text-gray-100">C</strong></li>
              <li className="flex items-center gap-2"><span className="text-xl">🐍</span> Practical scripting and ML exploration with <strong className="text-gray-900 dark:text-gray-100">Python</strong></li>
              <li className="flex items-center gap-2"><span className="text-xl">🛢️</span> Building scalable apps using <strong className="text-gray-900 dark:text-gray-100">MongoDB</strong> and <strong className="text-gray-900 dark:text-gray-100">PostgreSQL</strong></li>
              <li className="flex items-center gap-2"><span className="text-xl">🐧</span> Living the <strong className="text-gray-900 dark:text-gray-100">Linux</strong> terminal life</li>
            </ul>
            <p className="mt-4 italic text-sm opacity-80">
              I love turning bugs into features and ideas into side-projects.
            </p>
          </section>

          {/* Looking For section with a clean, centered layout */}
          <section className="text-center">
            <h3 className="text-2xl font-bold mb-4 flex items-center justify-center gap-2">
              <span role="img" aria-label="handshake-emoji">🤝</span> Looking For
            </h3>
            <div className="flex flex-col sm:flex-row justify-center gap-4">
              <div className="bg-indigo-50 dark:bg-indigo-900 p-6 rounded-xl shadow-md transform hover:scale-105 transition-transform duration-300">
                <p className="text-lg font-semibold text-indigo-700 dark:text-indigo-300">Collaboration</p>
                <p className="mt-2 text-sm opacity-90">on unique CLI tools, system daemons, or DB-backed apps.</p>
              </div>
              <div className="bg-purple-50 dark:bg-purple-900 p-6 rounded-xl shadow-md transform hover:scale-105 transition-transform duration-300">
                <p className="text-lg font-semibold text-purple-700 dark:text-purple-300">Mentorship</p>
                <p className="mt-2 text-sm opacity-90">in writing clean, maintainable code and system design.</p>
              </div>
            </div>
            <blockquote className="mt-8 text-sm italic opacity-70 border-l-4 border-gray-400 pl-4">
              “Code isn’t just code—it’s a conversation with your future self.”
            </blockquote>
          </section>

          {/* Tech Toolbox with interactive tooltips */}
          <section>
            <h3 className="text-2xl font-bold mb-4 flex items-center gap-2">
              <span role="img" aria-label="wrench-emoji">🧰</span> Tech Toolbox
            </h3>
            <div className="grid grid-cols-3 sm:grid-cols-4 md:grid-cols-7 gap-4">
              {techStack.map((tech, index) => (
                <div
                  key={index}
                  className="relative flex justify-center items-center p-2 rounded-xl bg-gray-100 dark:bg-gray-700 shadow-sm transition-all duration-300 transform hover:scale-110 cursor-pointer"
                  onMouseEnter={() => setHoveredTech(tech)}
                  onMouseLeave={() => setHoveredTech(null)}
                >
                  <img src={tech.icon} alt={tech.name} className="w-10 h-10" />
                  {hoveredTech && hoveredTech.name === tech.name && (
                    <div className="absolute top-1/2 left-1/2 -translate-x-1/2 mt-12 px-4 py-2 bg-gray-800 text-white text-xs rounded-lg shadow-lg whitespace-nowrap opacity-0 animate-fade-in z-20">
                      {tech.description}
                    </div>
                  )}
                </div>
              ))}
            </div>
          </section>

          {/* GitHub Stats & Activity */}
          <section className="bg-gray-50 dark:bg-gray-700 p-6 rounded-2xl shadow-inner transition-colors duration-500">
            <h3 className="text-2xl font-bold mb-4 flex items-center gap-2">
              <span role="img" aria-label="chart-emoji">📈</span> GitHub Stats & Activity
            </h3>
            <div className="flex flex-col sm:flex-row justify-center gap-4">
              <img
                src="https://github-readme-stats.vercel.app/api?username=alphawastaken&show_icons=true&theme=default&hide_title=true&count_private=true"
                alt="GitHub Stats"
                className="w-full sm:w-1/2 rounded-xl shadow-lg transform hover:scale-105 transition-transform duration-300"
              />
              <img
                src="https://github-readme-stats.vercel.app/api/top-langs/?username=alphawastaken&layout=compact&langs_count=8&theme=default"
                alt="Top Languages"
                className="w-full sm:w-1/2 rounded-xl shadow-lg transform hover:scale-105 transition-transform duration-300"
              />
            </div>
          </section>

          {/* Streak, Trophies, and Snake */}
          <section>
            <h3 className="text-2xl font-bold mb-4 flex items-center gap-2">
              <span role="img" aria-label="fire-emoji">🔥</span> Streak & Trophies
            </h3>
            <div className="flex flex-col sm:flex-row justify-center gap-4">
              <img
                src="https://streak-stats.demolab.com/?user=alphawastaken&theme=default"
                alt="GitHub Streak"
                className="w-full sm:w-1/2 rounded-xl shadow-lg transform hover:scale-105 transition-transform duration-300"
              />
              <img
                src="https://github-profile-trophy.vercel.app/?username=alphawastaken&theme=flat&no-bg=true&margin-w=10"
                alt="GitHub Trophies"
                className="w-full sm:w-1/2 rounded-xl shadow-lg transform hover:scale-105 transition-transform duration-300"
              />
            </div>
            <div className="mt-8 text-center">
              <h3 className="text-2xl font-bold mb-4 flex items-center justify-center gap-2">
                <span role="img" aria-label="snake-emoji">🐍</span> Snake Game of Contributions
              </h3>
              <picture className="inline-block rounded-xl shadow-lg overflow-hidden transform hover:scale-105 transition-transform duration-300">
                <source media="(prefers-color-scheme: dark)" srcSet="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake-dark.svg" />
                <source media="(prefers-color-scheme: light)" srcSet="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake.svg" />
                <img alt="GitHub Snake animation" src="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake.svg" className="w-full" />
              </picture>
            </div>
          </section>

          {/* A new, unique interactive button */}
          <section className="flex justify-center mt-12">
            <button
              onMouseEnter={() => setIsConnectHovered(true)}
              onMouseLeave={() => setIsConnectHovered(false)}
              className="relative py-3 px-8 text-lg font-bold text-white rounded-full bg-gradient-to-r from-blue-500 to-indigo-500 shadow-xl overflow-hidden transform transition-all duration-300 hover:scale-105 focus:outline-none focus:ring-4 focus:ring-blue-300"
            >
              <span className={`relative z-10 transition-all duration-300 ${isConnectHovered ? 'text-transparent' : 'text-white'}`}>
                Say Hi! 👋
              </span>
              <span className={`absolute inset-0 flex items-center justify-center text-white text-sm font-normal transition-all duration-300 z-0 ${isConnectHovered ? 'opacity-100 scale-100' : 'opacity-0 scale-50'}`}>
                Check out my GitHub!
              </span>
            </button>
          </section>

        </div>
      </div>
    </div>
  );
};

// Add custom CSS for blinking cursor and pulse effect.
const style = document.createElement('style');
style.innerHTML = `
  @keyframes blink {
    50% {
      opacity: 0;
    }
  }
  .animate-blink {
    animation: blink 1s step-end infinite;
  }

  @keyframes pulse-slow {
    0%, 100% {
      transform: scale(1) translateY(0);
      opacity: 0.2;
    }
    50% {
      transform: scale(1.05) translateY(-5%);
      opacity: 0.3;
    }
  }
  .animate-pulse-slow {
    animation: pulse-slow 6s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  }
  
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .animate-fade-in {
    animation: fadeIn 0.3s ease-out forwards;
  }
`;
document.head.appendChild(style);

// Mount the App component to the DOM.
document.addEventListener('DOMContentLoaded', () => {
    const rootElement = document.getElementById('root');
    if (rootElement) {
      createRoot(rootElement).render(<App />);
    } else {
      console.error("Root element not found");
    }
});

// React entry point - not rendered here but for the Canvas environment.
export default App;
