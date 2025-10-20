import React, { useState } from 'react';
import { Heart, Home, BookOpen, User, Play, Clock, Trophy, Volume2, Users, MapPin, Car, MessageCircle, AlertCircle, Phone, Cloud, Calendar, Video, Image, Mic, UserPlus, Share2, Award, Apple } from 'lucide-react';

export default function ActiveAgeApp() {
  const [currentView, setCurrentView] = useState('home');
  const [selectedExercise, setSelectedExercise] = useState(null);
  const [completedExercises, setCompletedExercises] = useState([]);
  const [streak, setStreak] = useState(3);
  const [selectedPost, setSelectedPost] = useState(null);
  const [showEmergency, setShowEmergency] = useState(false);
  const [showVideoCall, setShowVideoCall] = useState(false);
  const [showGallery, setShowGallery] = useState(false);
  const [showAchievements, setShowAchievements] = useState(false);
  const [showShareProgress, setShowShareProgress] = useState(false);
  
  const weatherData = {
    temp: 18,
    condition: 'Teilweise bewölkt',
    icon: Cloud,
    recommendation: 'Perfekt für Nordic Walking!'
  };

  const upcomingEvents = [
    { id: 1, title: 'Nordic Walking Gruppe', date: 'Mittwoch, 10:00', location: 'Stadtgarten' },
    { id: 2, title: 'Aqua-Fitness', date: 'Donnerstag, 9:30', location: 'Schwimmhalle' },
    { id: 3, title: 'Tischtennis-Runde', date: 'Freitag, 14:00', location: 'Gemeindezentrum' }
  ];

  const exercises = [
    {
      id: 1,
      title: 'Gleichgewichtsübung',
      category: 'Balance',
      duration: '5 Min',
      difficulty: 'Leicht',
      description: 'Verbessern Sie Ihr Gleichgewicht und beugen Sie Stürzen vor.',
      steps: [
        'Stellen Sie sich hinter einen stabilen Stuhl',
        'Halten Sie sich am Stuhl fest',
        'Heben Sie ein Bein langsam an (10 Sekunden halten)',
        'Wechseln Sie das Bein',
        'Wiederholen Sie 5x pro Seite'
      ],
      benefits: 'Sturzprävention, bessere Körperkontrolle'
    },
    {
      id: 2,
      title: 'Sitzende Armkreise',
      category: 'Mobilität',
      duration: '3 Min',
      difficulty: 'Sehr leicht',
      description: 'Lockern Sie Ihre Schultern und verbessern Sie die Beweglichkeit.',
      steps: [
        'Setzen Sie sich aufrecht auf einen Stuhl',
        'Strecken Sie beide Arme zur Seite aus',
        'Machen Sie langsame Kreise vorwärts (10x)',
        'Dann Kreise rückwärts (10x)',
        'Atmen Sie dabei ruhig weiter'
      ],
      benefits: 'Schulterflexibilität, Durchblutung'
    },
    {
      id: 3,
      title: 'Beinlifts im Sitzen',
      category: 'Kraft',
      duration: '4 Min',
      difficulty: 'Leicht',
      description: 'Stärken Sie Ihre Beinmuskulatur bequem im Sitzen.',
      steps: [
        'Setzen Sie sich auf die vordere Stuhlkante',
        'Strecken Sie ein Bein gerade aus',
        'Halten Sie 5 Sekunden',
        'Senken Sie das Bein langsam ab',
        'Wiederholen Sie 10x pro Bein'
      ],
      benefits: 'Beinmuskulatur, Kniestabilität'
    },
    {
      id: 4,
      title: 'Nackenentspannung',
      category: 'Entspannung',
      duration: '3 Min',
      difficulty: 'Sehr leicht',
      description: 'Lösen Sie Verspannungen im Nackenbereich.',
      steps: [
        'Sitzen oder stehen Sie aufrecht',
        'Neigen Sie den Kopf langsam zur rechten Seite',
        'Halten Sie 10 Sekunden',
        'Zurück zur Mitte, dann zur linken Seite',
        'Wiederholen Sie 5x pro Seite'
      ],
      benefits: 'Nackenentspannung, Kopfschmerzlinderung'
    }
  ];

  const communityPosts = [
    {
      id: 1,
      author: 'Maria K.',
      age: 68,
      location: 'Bottrop-Mitte',
      distance: '1.2 km',
      category: 'Sport',
      icon: '🚶‍♀️',
      title: 'Nordic Walking Gruppe am Stadtgarten',
      content: 'Wir treffen uns jeden Mittwoch um 10 Uhr am Stadtgarten-Eingang. Lockeres Tempo, mit Kaffeepause! Neue Gesichter willkommen 😊',
      time: 'vor 2 Stunden',
      participants: 5,
      comments: 3
    },
    {
      id: 2,
      author: 'Hans M.',
      age: 72,
      location: 'Bottrop-Kirchhellen',
      distance: '3.8 km',
      category: 'Fahrgemeinschaft',
      icon: '🚗',
      title: 'Fahrt zum Aqua-Fitness',
      content: 'Fahre jeden Dienstag und Donnerstag zur Schwimmhalle. Habe noch 2 Plätze frei. Abfahrt 9:00 Uhr.',
      time: 'vor 5 Stunden',
      participants: 2,
      comments: 1
    },
    {
      id: 3,
      author: 'Ingrid S.',
      age: 65,
      location: 'Bottrop-Süd',
      distance: '2.1 km',
      category: 'Gesundheit',
      icon: '🧘‍♀️',
      title: 'Rückengymnastik-Tipps gesucht',
      content: 'Hat jemand gute Erfahrungen mit Übungen gegen Rückenschmerzen? Würde mich gerne austauschen!',
      time: 'vor 1 Tag',
      participants: 0,
      comments: 7
    },
    {
      id: 4,
      author: 'Klaus W.',
      age: 70,
      location: 'Bottrop-Batenbrock',
      distance: '2.5 km',
      category: 'Sport',
      icon: '🎾',
      title: 'Tischtennis-Runde sucht Mitspieler',
      content: 'Wir spielen montags und freitags im Gemeindezentrum. Anfänger herzlich willkommen! Schläger vorhanden.',
      time: 'vor 3 Tagen',
      participants: 8,
      comments: 5
    }
  ];

  const familyContacts = [
    { id: 1, name: 'Anna (Tochter)', avatar: '👩', available: true },
    { id: 2, name: 'Michael (Sohn)', avatar: '👨', available: false },
    { id: 3, name: 'Emma (Enkelin)', avatar: '👧', available: true },
    { id: 4, name: 'Lisa (Schwester)', avatar: '👵', available: true },
    { id: 5, name: 'Peter (Bruder)', avatar: '👴', available: false },
    { id: 6, name: 'Beste Freundin Helga', avatar: '👩‍🦳', available: true }
  ];

  const photoGallery = [
    { id: 1, caption: 'Emmas Geburtstag', date: 'vor 3 Tagen', emoji: '🎉' },
    { id: 2, caption: 'Familienausflug zum See', date: 'vor 1 Woche', emoji: '🏞️' },
    { id: 3, caption: 'Omas Kuchen', date: 'vor 2 Wochen', emoji: '🍰' },
    { id: 4, caption: 'Gemeinsam im Garten', date: 'vor 3 Wochen', emoji: '🌻' },
    { id: 5, caption: 'Enkel Max spielt Fußball', date: 'vor 1 Monat', emoji: '⚽' },
    { id: 6, caption: 'Weihnachten 2024', date: 'vor 3 Monaten', emoji: '🎄' }
  ];

  const voiceMessages = [
    { id: 1, from: 'Emma', duration: '0:45', time: 'vor 2 Std.', unread: true },
    { id: 2, from: 'Anna', duration: '1:20', time: 'heute', unread: true },
    { id: 3, from: 'Michael', duration: '0:30', time: 'gestern', unread: false }
  ];

  const sharedExercises = [
    { id: 1, partner: 'Anna', exercise: 'Gleichgewichtsübung', date: 'Morgen, 10:00' },
    { id: 2, partner: 'Helga', exercise: 'Sitzende Armkreise', date: 'Freitag, 15:00' }
  ];

  const achievements = [
    { id: 1, title: '3-Tage Streak', icon: '🔥', unlocked: true, description: '3 Tage in Folge trainiert' },
    { id: 2, title: 'Erste Übung', icon: '🎯', unlocked: true, description: 'Erste Übung abgeschlossen' },
    { id: 3, title: 'Community-Mitglied', icon: '👥', unlocked: true, description: 'Erstes Community-Treffen' },
    { id: 4, title: '7-Tage Streak', icon: '⭐', unlocked: false, description: 'Noch 4 Tage bis zum Ziel!' },
    { id: 5, title: '10 Übungen', icon: '💪', unlocked: false, description: 'Noch 6 Übungen fehlen' },
    { id: 6, title: 'Familien-Training', icon: '👨‍👩‍👧', unlocked: true, description: 'Mit Familie trainiert' }
  ];

  const nutritionTips = [
    { id: 1, category: 'Frühstück', emoji: '🥣', tip: 'Haferflocken mit Beeren', benefit: 'Energie für den Tag' },
    { id: 2, category: 'Zwischenmahlzeit', emoji: '🥜', tip: 'Handvoll Nüsse', benefit: 'Gesunde Fette' },
    { id: 3, category: 'Mittagessen', emoji: '🥗', tip: 'Bunter Salat mit Fisch', benefit: 'Omega-3 & Vitamine' },
    { id: 4, category: 'Trinken', emoji: '💧', tip: '2-3 Liter Wasser täglich', benefit: 'Hydration' }
  ];

  const weeklyStats = {
    exercisesCompleted: 12,
    minutesActive: 85,
    caloriesBurned: 420,
    weekGoal: 15
  };

  const markComplete = (exerciseId) => {
    if (!completedExercises.includes(exerciseId)) {
      setCompletedExercises([...completedExercises, exerciseId]);
    }
  };

  const HomeView = () => (
    <div className="p-6 space-y-6">
      <div className="bg-gradient-to-r from-blue-500 to-blue-600 rounded-3xl p-8 text-white">
        <h1 className="text-4xl font-bold mb-3">Hallo! 👋</h1>
        <p className="text-2xl mb-6">Schön, dass Sie da sind!</p>
        <div className="flex items-center gap-4 bg-white/20 rounded-2xl p-4">
          <Trophy className="w-12 h-12" />
          <div>
            <p className="text-xl font-semibold">{streak} Tage Streak! 🔥</p>
            <p className="text-lg">Großartig gemacht!</p>
          </div>
        </div>
      </div>

      <button
        onClick={() => setShowEmergency(true)}
        className="w-full bg-red-500 hover:bg-red-600 text-white rounded-3xl p-6 flex items-center justify-center gap-4 transition-all shadow-lg"
      >
        <AlertCircle className="w-16 h-16" />
        <div className="text-left">
          <p className="text-3xl font-bold">NOTFALL</p>
          <p className="text-xl">Hilfe rufen</p>
        </div>
      </button>

      <div className="bg-gradient-to-r from-orange-400 to-red-400 rounded-3xl p-6 text-white">
        <div className="flex items-center justify-between mb-4">
          <div className="flex items-center gap-3">
            <Apple className="w-12 h-12" />
            <h2 className="text-3xl font-bold">Ernährungstipp</h2>
          </div>
        </div>
        <div className="bg-white/20 rounded-2xl p-5">
          <div className="flex items-start gap-4">
            <span className="text-5xl">{nutritionTips[0].emoji}</span>
            <div>
              <p className="text-2xl font-bold mb-2">{nutritionTips[0].tip}</p>
              <p className="text-xl">{nutritionTips[0].category}</p>
              <p className="text-lg mt-2">✨ {nutritionTips[0].benefit}</p>
            </div>
          </div>
        </div>
        <button 
          onClick={() => setCurrentView('nutrition')}
          className="w-full bg-white/30 hover:bg-white/40 text-white text-xl font-bold py-3 rounded-2xl mt-4 transition-all"
        >
          Alle Tipps ansehen
        </button>
      </div>

      <div className="bg-gradient-to-r from-cyan-400 to-blue-400 rounded-3xl p-6 text-white">
        <div className="flex items-center justify-between mb-3">
          <h2 className="text-3xl font-bold">Wetter heute</h2>
          <weatherData.icon className="w-14 h-14" />
        </div>
        <p className="text-5xl font-bold mb-2">{weatherData.temp}°C</p>
        <p className="text-2xl mb-3">{weatherData.condition}</p>
        <div className="bg-white/20 rounded-2xl p-4">
          <p className="text-xl font-semibold">💡 {weatherData.recommendation}</p>
        </div>
      </div>

      <div className="bg-white border-4 border-gray-200 rounded-3xl p-6">
        <div className="flex items-center gap-3 mb-4">
          <Calendar className="w-10 h-10 text-purple-600" />
          <h2 className="text-3xl font-bold">Ihre Termine</h2>
        </div>
        <div className="space-y-3">
          {upcomingEvents.map(event => (
            <div key={event.id} className="bg-purple-50 rounded-2xl p-4 border-2 border-purple-200">
              <p className="text-2xl font-bold text-purple-900">{event.title}</p>
              <p className="text-xl text-purple-700 mt-1">{event.date}</p>
              <p className="text-lg text-purple-600 flex items-center gap-2 mt-1">
                <MapPin className="w-5 h-5" />
                {event.location}
              </p>
            </div>
          ))}
        </div>
      </div>

      <div className="grid grid-cols-2 gap-4">
        <button
          onClick={() => setCurrentView('exercises')}
          className="bg-blue-500 hover:bg-blue-600 text-white rounded-3xl p-8 flex flex-col items-center justify-center gap-3 transition-all"
        >
          <Play className="w-16 h-16" />
          <span className="text-2xl font-bold">Übungen starten</span>
        </button>
        <button
          onClick={() => setShowVideoCall(true)}
          className="bg-green-500 hover:bg-green-600 text-white rounded-3xl p-8 flex flex-col items-center justify-center gap-3 transition-all"
        >
          <Video className="w-16 h-16" />
          <span className="text-2xl font-bold">Video-Anruf</span>
        </button>
      </div>
    </div>
  );

  const ExercisesView = () => (
    <div className="p-6 space-y-4">
      <h1 className="text-4xl font-bold mb-6">Ihre Übungen</h1>
      {exercises.map(exercise => (
        <button
          key={exercise.id}
          onClick={() => {
            setSelectedExercise(exercise);
            setCurrentView('detail');
          }}
          className="w-full bg-white border-4 border-gray-200 rounded-3xl p-6 text-left hover:border-blue-400 transition-all"
        >
          <div className="flex justify-between items-start mb-3">
            <h3 className="text-3xl font-bold text-gray-800">{exercise.title}</h3>
            {completedExercises.includes(exercise.id) && (
              <span className="text-4xl">✓</span>
            )}
          </div>
          <div className="flex flex-wrap gap-3 mb-3">
            <span className="bg-blue-100 text-blue-800 px-4 py-2 rounded-full text-xl font-semibold">
              {exercise.category}
            </span>
            <span className="bg-green-100 text-green-800 px-4 py-2 rounded-full text-xl font-semibold">
              {exercise.difficulty}
            </span>
            <span className="bg-purple-100 text-purple-800 px-4 py-2 rounded-full text-xl font-semibold flex items-center gap-2">
              <Clock className="w-5 h-5" />
              {exercise.duration}
            </span>
          </div>
          <p className="text-2xl text-gray-600">{exercise.description}</p>
        </button>
      ))}
    </div>
  );

  const ExerciseDetailView = () => (
    <div className="p-6 space-y-6">
      <button
        onClick={() => setCurrentView('exercises')}
        className="text-3xl text-blue-600 font-semibold mb-4"
      >
        ← Zurück
      </button>
      
      <div className="bg-gradient-to-r from-blue-500 to-purple-500 rounded-3xl p-8 text-white">
        <h1 className="text-4xl font-bold mb-4">{selectedExercise.title}</h1>
        <div className="flex flex-wrap gap-3">
          <span className="bg-white/30 px-4 py-2 rounded-full text-xl font-semibold">
            {selectedExercise.duration}
          </span>
          <span className="bg-white/30 px-4 py-2 rounded-full text-xl font-semibold">
            {selectedExercise.difficulty}
          </span>
        </div>
      </div>

      <div className="bg-gradient-to-r from-green-400 to-blue-400 rounded-3xl p-6 text-white">
        <div className="flex items-center gap-3 mb-4">
          <UserPlus className="w-10 h-10" />
          <h2 className="text-2xl font-bold">Familie einladen</h2>
        </div>
        <p className="text-xl mb-4">Trainieren Sie gemeinsam mit Ihrer Familie per Video-Call!</p>
        <button className="w-full bg-white text-green-700 text-2xl font-bold py-4 rounded-2xl hover:bg-green-50 transition-all">
          Jetzt Familie einladen
        </button>
      </div>

      <div className="bg-yellow-50 border-4 border-yellow-200 rounded-3xl p-6">
        <h2 className="text-3xl font-bold text-yellow-900 mb-4 flex items-center gap-3">
          <Volume2 className="w-10 h-10" />
          Sprachanleitung
        </h2>
        <button className="bg-yellow-500 hover:bg-yellow-600 text-white text-2xl font-bold py-4 px-8 rounded-2xl">
          Anleitung vorlesen
        </button>
      </div>

      <div className="bg-white border-4 border-gray-200 rounded-3xl p-6">
        <h2 className="text-3xl font-bold mb-4">📋 So geht's:</h2>
        <ol className="space-y-4">
          {selectedExercise.steps.map((step, index) => (
            <li key={index} className="flex gap-4">
              <span className="bg-blue-500 text-white w-12 h-12 rounded-full flex items-center justify-center text-2xl font-bold flex-shrink-0">
                {index + 1}
              </span>
              <p className="text-2xl text-gray-800 pt-2">{step}</p>
            </li>
          ))}
        </ol>
      </div>

      <div className="bg-green-50 border-4 border-green-200 rounded-3xl p-6">
        <h2 className="text-3xl font-bold text-green-800 mb-3">✨ Vorteile:</h2>
        <p className="text-2xl text-green-900">{selectedExercise.benefits}</p>
      </div>

      <button
        onClick={() => {
          markComplete(selectedExercise.id);
          setCurrentView('exercises');
        }}
        className="w-full bg-green-500 hover:bg-green-600 text-white text-3xl font-bold py-6 rounded-3xl transition-all"
      >
        ✓ Übung abschließen
      </button>
    </div>
  );

  const CommunityView = () => (
    <div className="p-6 space-y-6">
      <h1 className="text-4xl font-bold mb-4">Gemeinschaft</h1>
      <p className="text-2xl text-gray-600 mb-6">Vernetzen Sie sich mit aktiven Menschen in Ihrer Nähe!</p>

      <div className="flex gap-3 overflow-x-auto pb-2">
        <button className="bg-blue-500 text-white px-6 py-3 rounded-2xl text-xl font-semibold whitespace-nowrap">
          Alle
        </button>
        <button className="bg-gray-200 text-gray-700 px-6 py-3 rounded-2xl text-xl font-semibold whitespace-nowrap">
          🚶‍♀️ Sport
        </button>
        <button className="bg-gray-200 text-gray-700 px-6 py-3 rounded-2xl text-xl font-semibold whitespace-nowrap">
          🧘‍♀️ Gesundheit
        </button>
        <button className="bg-gray-200 text-gray-700 px-6 py-3 rounded-2xl text-xl font-semibold whitespace-nowrap">
          🚗 Fahrgemeinschaft
        </button>
      </div>

      <button className="w-full bg-green-500 hover:bg-green-600 text-white text-2xl font-bold py-5 rounded-3xl transition-all">
        + Eigenen Beitrag erstellen
      </button>

      <div className="space-y-4">
        {communityPosts.map(post => (
          <button
            key={post.id}
            onClick={() => {
              setSelectedPost(post);
              setCurrentView('post-detail');
            }}
            className="w-full bg-white border-4 border-gray-200 rounded-3xl p-6 text-left hover:border-blue-400 transition-all"
          >
            <div className="flex items-start gap-4 mb-4">
              <div className="text-5xl">{post.icon}</div>
              <div className="flex-1">
                <div className="flex justify-between items-start mb-2">
                  <div>
                    <h3 className="text-2xl font-bold text-gray-800">{post.author}, {post.age}</h3>
                    <div className="flex items-center gap-2 text-xl text-gray-600 mt-1">
                      <MapPin className="w-5 h-5" />
                      <span>{post.location} • {post.distance}</span>
                    </div>
                  </div>
                  <span className="bg-blue-100 text-blue-800 px-3 py-1 rounded-full text-lg font-semibold">
                    {post.category}
                  </span>
                </div>
              </div>
            </div>
            
            <h4 className="text-2xl font-bold text-gray-900 mb-2">{post.title}</h4>
            <p className="text-xl text-gray-700 mb-4">{post.content}</p>
            
            <div className="flex items-center gap-6 text-gray-600 text-lg border-t-2 border-gray-200 pt-3">
              <span>{post.time}</span>
              <span className="flex items-center gap-2">
                <Users className="w-5 h-5" />
                {post.participants} dabei
              </span>
              <span className="flex items-center gap-2">
                <MessageCircle className="w-5 h-5" />
                {post.comments} Kommentare
              </span>
            </div>
          </button>
        ))}
      </div>
    </div>
  );

  const PostDetailView = () => (
    <div className="p-6 space-y-6">
      <button
        onClick={() => setCurrentView('community')}
        className="text-3xl text-blue-600 font-semibold mb-4"
      >
        ← Zurück
      </button>

      <div className="bg-white border-4 border-gray-200 rounded-3xl p-6">
        <div className="flex items-start gap-4 mb-4">
          <div className="text-6xl">{selectedPost.icon}</div>
          <div className="flex-1">
            <h3 className="text-3xl font-bold text-gray-800 mb-2">{selectedPost.author}, {selectedPost.age}</h3>
            <div className="flex items-center gap-2 text-2xl text-gray-600">
              <MapPin className="w-6 h-6" />
              <span>{selectedPost.location} • {selectedPost.distance} entfernt</span>
            </div>
          </div>
        </div>

        <span className="inline-block bg-blue-100 text-blue-800 px-4 py-2 rounded-full text-xl font-semibold mb-4">
          {selectedPost.category}
        </span>

        <h2 className="text-3xl font-bold text-gray-900 mb-4">{selectedPost.title}</h2>
        <p className="text-2xl text-gray-700 leading-relaxed mb-6">{selectedPost.content}</p>

        <div className="flex items-center gap-6 text-gray-600 text-xl border-t-2 border-gray-200 pt-4">
          <span>{selectedPost.time}</span>
          <span className="flex items-center gap-2">
            <Users className="w-6 h-6" />
            {selectedPost.participants} Teilnehmer
          </span>
        </div>
      </div>

      <div className="grid grid-cols-2 gap-4">
        <button className="bg-green-500 hover:bg-green-600 text-white text-2xl font-bold py-5 rounded-3xl transition-all">
          ✓ Mitmachen
        </button>
        <button className="bg-blue-500 hover:bg-blue-600 text-white text-2xl font-bold py-5 rounded-3xl transition-all flex items-center justify-center gap-2">
          <MessageCircle className="w-7 h-7" />
          Nachricht
        </button>
      </div>

      <div className="bg-gray-50 border-4 border-gray-200 rounded-3xl p-6">
        <h3 className="text-2xl font-bold mb-4">💬 Kommentare ({selectedPost.comments})</h3>
        <div className="space-y-4">
          <div className="bg-white rounded-2xl p-4">
            <p className="text-xl font-semibold mb-1">Petra L.</p>
            <p className="text-xl text-gray-700">Das klingt super! Bin gerne dabei 😊</p>
            <p className="text-lg text-gray-500 mt-2">vor 1 Stunde</p>
          </div>
          <div className="bg-white rounded-2xl p-4">
            <p className="text-xl font-semibold mb-1">Werner H.</p>
            <p className="text-xl text-gray-700">Tolle Initiative! Ich komme auch mit.</p>
            <p className="text-lg text-gray-500 mt-2">vor 3 Stunden</p>
          </div>
        </div>
        
        <button className="w-full bg-blue-500 hover:bg-blue-600 text-white text-xl font-bold py-4 rounded-2xl mt-4 transition-all">
          Kommentar schreiben
        </button>
      </div>
    </div>
  );

  const NutritionView = () => (
    <div className="p-6 space-y-6">
      <button
        onClick={() => setCurrentView('home')}
        className="text-3xl text-blue-600 font-semibold mb-4"
      >
        ← Zurück
      </button>

      <div className="bg-gradient-to-r from-orange-400 to-red-400 rounded-3xl p-8 text-white text-center">
        <Apple className="w-20 h-20 mx-auto mb-4" />
        <h1 className="text-4xl font-bold mb-3">Ernährungstipps</h1>
        <p className="text-2xl">Gesund essen, fit bleiben!</p>
      </div>

      <div className="space-y-4">
        {nutritionTips.map(tip => (
          <div key={tip.id} className="bg-white border-4 border-orange-200 rounded-3xl p-6">
            <div className="flex items-start gap-4">
              <span className="text-6xl">{tip.emoji}</span>
              <div className="flex-1">
                <span className="inline-block bg-orange-100 text-orange-800 px-4 py-2 rounded-full text-lg font-semibold mb-3">
                  {tip.category}
                </span>
                <h3 className="text-3xl font-bold text-gray-800 mb-2">{tip.tip}</h3>
                <p className="text-2xl text-gray-600">✨ {tip.benefit}</p>
              </div>
            </div>
          </div>
        ))}
      </div>

      <div className="bg-green-50 border-4 border-green-200 rounded-3xl p-6">
        <h2 className="text-3xl font-bold text-green-800 mb-4">💡 Wichtig zu wissen</h2>
        <ul className="space-y-3 text-2xl text-green-900">
          <li>• Ausgewogene Ernährung ist wichtig</li>
          <li>• Regelmäßige Mahlzeiten helfen</li>
          <li>• Viel Gemüse und Obst essen</li>
          <li>• Ausreichend trinken nicht vergessen</li>
        </ul>
      </div>
    </div>
  );

  const ProfileView = () => (
    <div className="p-6 space-y-6">
      <h1 className="text-4xl font-bold mb-6">Ihr Profil</h1>
      
      <div className="bg-gradient-to-r from-purple-500 to-pink-500 rounded-3xl p-8 text-white text-center">
        <div className="w-32 h-32 bg-white rounded-full mx-auto mb-4 flex items-center justify-center">
          <User className="w-20 h-20 text-purple-500" />
        </div>
        <h2 className="text-3xl font-bold mb-2">Aktiver Nutzer</h2>
        <p className="text-2xl">Mitglied seit Oktober 2025</p>
      </div>

      <div className="grid grid-cols-2 gap-4">
        <div className="bg-blue-50 border-4 border-blue-200 rounded-3xl p-6 text-center">
          <Trophy className="w-16 h-16 text-blue-600 mx-auto mb-3" />
          <p className="text-5xl font-bold text-blue-600 mb-2">{streak}</p>
          <p className="text-2xl text-blue-800">Tage Streak</p>
        </div>
        <button
          onClick={() => setShowAchievements(true)}
          className="bg-yellow-400 hover:bg-yellow-500 border-4 border-yellow-500 rounded-3xl p-6 text-center transition-all relative"
        >
          <Award className="w-16 h-16 text-yellow-900 mx-auto mb-3" />
          <p className="text-5xl font-bold text-yellow-900 mb-2">{achievements.filter(a => a.unlocked).length}</p>
          <p className="text-2xl text-yellow-900 font-bold">Erfolge</p>
          <div className="absolute top-2 right-2 bg-red-500 text-white w-7 h-7 rounded-full flex items-center justify-center text-sm font-bold">
            NEU
          </div>
        </button>
      </div>

      <button
        onClick={() => setShowShareProgress(true)}
        className="w-full bg-gradient-to-r from-purple-500 to-pink-500 hover:from-purple-600 hover:to-pink-600 text-white rounded-3xl p-6 flex items-center justify-center gap-4 transition-all"
      >
        <Share2 className="w-12 h-12" />
        <div className="text-left">
          <p className="text-2xl font-bold">Fortschritt teilen</p>
          <p className="text-lg">Familie stolz machen! 🎉</p>
        </div>
      </button>

      <div className="grid grid-cols-2 gap-4">
        <button 
          onClick={() => setShowGallery(true)}
          className="bg-pink-500 hover:bg-pink-600 text-white rounded-3xl p-6 flex flex-col items-center justify-center gap-3 transition-all"
        >
          <Image className="w-12 h-12" />
          <span className="text-xl font-bold">Foto-Galerie</span>
        </button>
        <button className="bg-orange-500 hover:bg-orange-600 text-white rounded-3xl p-6 flex flex-col items-center justify-center gap-3 transition-all relative">
          <Mic className="w-12 h-12" />
          <span className="text-xl font-bold">Sprachnachrichten</span>
          {voiceMessages.filter(m => m.unread).length > 0 && (
            <div className="absolute top-3 right-3 bg-red-500 text-white w-8 h-8 rounded-full flex items-center justify-center text-lg font-bold">
              {voiceMessages.filter(m => m.unread).length}
            </div>
          )}
        </button>
      </div>

      <div className="bg-white border-4 border-blue-200 rounded-3xl p-6">
        <div className="flex items-center gap-3 mb-4">
          <UserPlus className="w-10 h-10 text-blue-600" />
          <h2 className="text-3xl font-bold">Gemeinsam trainieren</h2>
        </div>
        {sharedExercises.length > 0 ? (
          <div className="space-y-3 mb-4">
            {sharedExercises.map(session => (
              <div key={session.id} className="bg-blue-50 rounded-2xl p-4 border-2 border-blue-200">
                <p className="text-2xl font-bold text-blue-900">Mit {session.partner}</p>
                <p className="text-xl text-blue-700 mt-1">{session.exercise}</p>
                <p className="text-lg text-blue-600 flex items-center gap-2 mt-1">
                  <Clock className="w-5 h-5" />
                  {session.date}
                </p>
              </div>
            ))}
          </div>
        ) : (
          <p className="text-xl text-gray-600 mb-4">Noch keine gemeinsamen Übungen geplant</p>
        )}
        <button className="w-full bg-blue-500 hover:bg-blue-600 text-white text-2xl font-bold py-4 rounded-2xl transition-all">
          + Familie einladen
        </button>
      </div>

      <div className="bg-white border-4 border-gray-200 rounded-3xl p-6">
        <h2 className="text-3xl font-bold mb-4">⚙️ Einstellungen</h2>
        <div className="space-y-4">
          <button className="w-full bg-gray-100 hover:bg-gray-200 text-2xl font-semibold py-5 px-6 rounded-2xl text-left transition-all">
            Textgröße anpassen
          </button>
          <button className="w-full bg-gray-100 hover:bg-gray-200 text-2xl font-semibold py-5 px-6 rounded-2xl text-left transition-all">
            Sprachsteuerung aktivieren
          </button>
          <button className="w-full bg-gray-100 hover:bg-gray-200 text-2xl font-semibold py-5 px-6 rounded-2xl text-left transition-all">
            Erinnerungen einstellen
          </button>
        </div>
      </div>
    </div>
  );

  return (
    <div className="max-w-2xl mx-auto bg-gray-50 min-h-screen flex flex-col">
      <div className="flex-1 overflow-y-auto pb-24">
        {currentView === 'home' && <HomeView />}
        {currentView === 'exercises' && <ExercisesView />}
        {currentView === 'detail' && selectedExercise && <ExerciseDetailView />}
        {currentView === 'community' && <CommunityView />}
        {currentView === 'post-detail' && selectedPost && <PostDetailView />}
        {currentView === 'nutrition' && <NutritionView />}
        {currentView === 'profile' && <ProfileView />}
      </div>

      <nav className="fixed bottom-0 left-0 right-0 max-w-2xl mx-auto bg-white border-t-4 border-gray-200">
        <div className="flex justify-around py-4">
          <button
            onClick={() => setCurrentView('home')}
            className={`flex flex-col items-center gap-2 px-4 py-3 rounded-2xl transition-all ${
              currentView === 'home' ? 'bg-blue-100 text-blue-600' : 'text-gray-600'
            }`}
          >
            <Home className="w-10 h-10" />
            <span className="text-lg font-semibold">Start</span>
          </button>
          <button
            onClick={() => setCurrentView('exercises')}
            className={`flex flex-col items-center gap-2 px-4 py-3 rounded-2xl transition-all ${
              currentView === 'exercises' || currentView === 'detail' ? 'bg-blue-100 text-blue-600' : 'text-gray-600'
            }`}
          >
            <BookOpen className="w-10 h-10" />
            <span className="text-lg font-semibold">Übungen</span>
          </button>
          <button
            onClick={() => setCurrentView('community')}
            className={`flex flex-col items-center gap-2 px-4 py-3 rounded-2xl transition-all ${
              currentView === 'community' || currentView === 'post-detail' ? 'bg-blue-100 text-blue-600' : 'text-gray-600'
            }`}
          >
            <Users className="w-10 h-10" />
            <span className="text-lg font-semibold">Community</span>
          </button>
          <button
            onClick={() => setCurrentView('profile')}
            className={`flex flex-col items-center gap-2 px-4 py-3 rounded-2xl transition-all ${
              currentView === 'profile' ? 'bg-blue-100 text-blue-600' : 'text-gray-600'
            }`}
          >
            <User className="w-10 h-10" />
            <span className="text-lg font-semibold">Profil</span>
          </button>
        </div>
      </nav>

      {showEmergency && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-6">
          <div className="bg-white rounded-3xl p-8 max-w-lg w-full">
            <h2 className="text-4xl font-bold text-red-600 mb-6 text-center">NOTFALL</h2>
            <p className="text-2xl text-center mb-6">Brauchen Sie sofortige Hilfe?</p>
            
            <div className="space-y-4">
              <button className="w-full bg-red-500 hover:bg-red-600 text-white text-2xl font-bold py-6 rounded-2xl flex items-center justify-center gap-3 transition-all">
                <Phone className="w-8 h-8" />
                112 - Notruf
              </button>
              <button className="w-full bg-orange-500 hover:bg-orange-600 text-white text-2xl font-bold py-6 rounded-2xl flex items-center justify-center gap-3 transition-all">
                <Phone className="w-8 h-8" />
                116 117 - Ärztlicher Bereitschaftsdienst
              </button>
              <button className="w-full bg-blue-500 hover:bg-blue-600 text-white text-2xl font-bold py-6 rounded-2xl flex items-center justify-center gap-3 transition-all">
                <Phone className="w-8 h-8" />
                Notfallkontakt anrufen
              </button>
            </div>
            
            <button
              onClick={() => setShowEmergency(false)}
              className="w-full bg-gray-300 hover:bg-gray-400 text-gray-800 text-2xl font-bold py-5 rounded-2xl mt-6 transition-all"
            >
              Abbrechen
            </button>
          </div>
        </div>
      )}

      {showVideoCall && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-6">
          <div className="bg-white rounded-3xl p-8 max-w-2xl w-full max-h-[90vh] overflow-y-auto">
            <h2 className="text-4xl font-bold text-green-600 mb-6 text-center flex items-center justify-center gap-3">
              <Video className="w-12 h-12" />
              Video-Anruf starten
            </h2>
            <p className="text-2xl text-center mb-6 text-gray-600">Wählen Sie einen Kontakt aus:</p>
            
            <div className="grid grid-cols-2 gap-4 mb-6">
              {familyContacts.map(contact => (
                <button
                  key={contact.id}
                  disabled={!contact.available}
                  className={`rounded-3xl p-6 flex flex-col items-center gap-3 transition-all ${
                    contact.available 
                      ? 'bg-green-100 hover:bg-green-200 border-4 border-green-300' 
                      : 'bg-gray-200 border-4 border-gray-300 opacity-60 cursor-not-allowed'
                  }`}
                >
                  <div className="text-6xl">{contact.avatar}</div>
                  <span className="text-xl font-bold text-gray-800 text-center">{contact.name}</span>
                  <div className="flex items-center gap-2">
                    <div className={`w-4 h-4 rounded-full ${contact.available ? 'bg-green-500' : 'bg-gray-400'}`}></div>
                    <span className="text-lg">{contact.available ? 'Online' : 'Offline'}</span>
                  </div>
                  {contact.available && (
                    <div className="w-full bg-green-500 text-white py-2 rounded-xl text-lg font-semibold flex items-center justify-center gap-2">
                      <Video className="w-5 h-5" />
                      Anrufen
                    </div>
                  )}
                </button>
              ))}
            </div>

            <div className="bg-blue-50 border-4 border-blue-200 rounded-2xl p-5 mb-6">
              <p className="text-xl text-blue-900 text-center">
                💡 <strong>Tipp:</strong> Grüner Punkt = Person ist gerade verfügbar
              </p>
            </div>
            
            <button
              onClick={() => setShowVideoCall(false)}
              className="w-full bg-gray-300 hover:bg-gray-400 text-gray-800 text-2xl font-bold py-5 rounded-2xl transition-all"
            >
              Schließen
            </button>
          </div>
        </div>
      )}

      {showGallery && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-6">
          <div className="bg-white rounded-3xl p-8 max-w-2xl w-full max-h-[90vh] overflow-y-auto">
            <h2 className="text-4xl font-bold text-pink-600 mb-6 text-center flex items-center justify-center gap-3">
              <Image className="w-12 h-12" />
              Familien-Fotos
            </h2>
            
            <div className="grid grid-cols-2 gap-4 mb-6">
              {photoGallery.map(photo => (
                <div key={photo.id} className="bg-gradient-to-br from-pink-100 to-purple-100 rounded-3xl p-6 border-4 border-pink-200">
                  <div className="text-7xl mb-4 text-center">{photo.emoji}</div>
                  <p className="text-xl font-bold text-gray-800 mb-2">{photo.caption}</p>
                  <p className="text-lg text-gray-600">{photo.date}</p>
                </div>
              ))}
            </div>

            <button className="w-full bg-pink-500 hover:bg-pink-600 text-white text-2xl font-bold py-5 rounded-2xl mb-4 transition-all">
              + Neues Foto hinzufügen
            </button>
            
            <button
              onClick={() => setShowGallery(false)}
              className="w-full bg-gray-300 hover:bg-gray-400 text-gray-800 text-2xl font-bold py-5 rounded-2xl transition-all"
            >
              Schließen
            </button>
          </div>
        </div>
      )}

      {showAchievements && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-6">
          <div className="bg-white rounded-3xl p-8 max-w-2xl w-full max-h-[90vh] overflow-y-auto">
            <h2 className="text-4xl font-bold text-yellow-600 mb-6 text-center flex items-center justify-center gap-3">
              <Award className="w-12 h-12" />
              Ihre Erfolge
            </h2>
            
            <div className="grid grid-cols-2 gap-4 mb-6">
              {achievements.map(achievement => (
                <div 
                  key={achievement.id} 
                  className={`rounded-3xl p-6 border-4 ${
                    achievement.unlocked 
                      ? 'bg-gradient-to-br from-yellow-100 to-orange-100 border-yellow-400' 
                      : 'bg-gray-100 border-gray-300 opacity-60'
                  }`}
                >
                  <div className="text-6xl mb-3 text-center">{achievement.icon}</div>
                  <p className="text-2xl font-bold text-gray-800 mb-2 text-center">{achievement.title}</p>
                  <p className="text-lg text-gray-600 text-center">{achievement.description}</p>
                  {achievement.unlocked && (
                    <div className="mt-3 bg-green-500 text-white text-lg font-bold py-2 rounded-xl text-center">
                      ✓ Freigeschaltet
                    </div>
                  )}
                </div>
              ))}
            </div>
            
            <button
              onClick={() => setShowAchievements(false)}
              className="w-full bg-gray-300 hover:bg-gray-400 text-gray-800 text-2xl font-bold py-5 rounded-2xl transition-all"
            >
              Schließen
            </button>
          </div>
        </div>
      )}

      {showShareProgress && (
        <div className="fixed inset-0 bg-black/50 flex items-center justify-center z-50 p-6">
          <div className="bg-white rounded-3xl p-8 max-w-2xl w-full max-h-[90vh] overflow-y-auto">
            <h2 className="text-4xl font-bold text-purple-600 mb-6 text-center flex items-center justify-center gap-3">
              <Share2 className="w-12 h-12" />
              Fortschritt teilen
            </h2>
            
            <div className="bg-gradient-to-r from-purple-100 to-pink-100 rounded-3xl p-6 mb-6 border-4 border-purple-200">
              <h3 className="text-3xl font-bold text-center mb-4">Diese Woche</h3>
              <div className="grid grid-cols-2 gap-4">
                <div className="bg-white rounded-2xl p-4 text-center">
                  <p className="text-5xl font-bold text-purple-600">{weeklyStats.exercisesCompleted}</p>
                  <p className="text-xl text-gray-700 mt-2">Übungen</p>
                </div>
                <div className="bg-white rounded-2xl p-4 text-center">
                  <p className="text-5xl font-bold text-blue-600">{weeklyStats.minutesActive}</p>
                  <p className="text-xl text-gray-700 mt-2">Minuten</p>
                </div>
              </div>
              <div className="mt-4 bg-white rounded-2xl p-4">
                <p className="text-2xl font-bold text-center text-green-600">
                  🎯 Ziel: {weeklyStats.exercisesCompleted}/{weeklyStats.weekGoal} Übungen
                </p>
                <div className="w-full bg-gray-200 rounded-full h-6 mt-3">
                  <div 
                    className="bg-green-500 h-6 rounded-full transition-all"
                    style={{ width: `${(weeklyStats.exercisesCompleted / weeklyStats.weekGoal) * 100}%` }}
                  ></div>
                </div>
              </div>
            </div>

            <p className="text-2xl text-center mb-4 text-gray-600">Mit wem möchten Sie teilen?</p>

            <div className="grid grid-cols-3 gap-3 mb-6">
              {familyContacts.slice(0, 6).map(contact => (
                <button
                  key={contact.id}
                  className="bg-purple-100 hover:bg-purple-200 border-4 border-purple-300 rounded-2xl p-4 flex flex-col items-center gap-2 transition-all"
                >
                  <div className="text-5xl">{contact.avatar}</div>
                  <span className="text-lg font-bold text-center">{contact.name.split('(')[0].trim()}</span>
                </button>
              ))}
            </div>

            <button className="w-full bg-purple-500 hover:bg-purple-600 text-white text-2xl font-bold py-5 rounded-2xl mb-4 transition-all">
              📤 Fortschritt senden
            </button>
            
            <button
              onClick={() => setShowShareProgress(false)}
              className="w-full bg-gray-300 hover:bg-gray-400 text-gray-800 text-2xl font-bold py-5 rounded-2xl transition-all"
            >
              Schließen
            </button>
          </div>
        </div>
      )}
    </div>
  );
}
