# UI

![[Screenshot 2025-02-24 at 10.15.37 PM.png]]

![[Screenshot 2025-02-24 at 10.56.22 PM.png]]

![[Screenshot 2025-02-24 at 10.57.00 PM.png]]

![[Screenshot 2025-02-24 at 10.57.21 PM.png]]

## Pollination Station UI Prototype

```
import React, { useState } from 'react';
import { Bell, Home, Users, FileText, Award, Plus, Search, ArrowRight, Zap } from 'lucide-react';

const PollinationStation = () => {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [showCreateModal, setShowCreateModal] = useState(false);

  const mockDAOs = [
    { id: 1, name: "ClimateDAO", description: "Funding climate projects", members: 342, proposals: 8, match: 92 },
    { id: 2, name: "EduDAO", description: "Improving educational access", members: 189, proposals: 5, match: 85 },
    { id: 3, name: "DevDAO", description: "Supporting open source developers", members: 567, proposals: 12, match: 78 },
    { id: 4, name: "ArtDAO", description: "Funding digital artists", members: 231, proposals: 6, match: 63 }
  ];

  const mockProposals = [
    { id: 1, title: "Joint Climate Hackathon", dao: "ClimateDAO", status: "Active", votes: 78, created: "2d ago" },
    { id: 2, title: "Educational Resource Sharing", dao: "EduDAO", status: "Draft", votes: 0, created: "5h ago" }
  ];

  return (
    <div className="flex h-screen bg-gray-100">
      {/* Sidebar */}
      <div className="w-64 bg-white shadow-md">
        <div className="p-4">
          <div className="flex items-center space-x-2">
            <div className="w-8 h-8 bg-gradient-to-r from-purple-500 to-pink-500 rounded-full"></div>
            <h1 className="text-xl font-bold text-gray-800">Pollination Station</h1>
          </div>
        </div>
        
        <nav className="mt-8">
          <div className={`flex items-center px-4 py-3 ${activeTab === 'dashboard' ? 'bg-purple-100 text-purple-700 border-r-4 border-purple-500' : 'text-gray-600'}`} onClick={() => setActiveTab('dashboard')}>
            <Home className="w-5 h-5 mr-3" />
            <span className="font-medium">Dashboard</span>
          </div>
          
          <div className={`flex items-center px-4 py-3 ${activeTab === 'myDAOs' ? 'bg-purple-100 text-purple-700 border-r-4 border-purple-500' : 'text-gray-600'}`} onClick={() => setActiveTab('myDAOs')}>
            <Users className="w-5 h-5 mr-3" />
            <span className="font-medium">My DAOs</span>
          </div>
          
          <div className={`flex items-center px-4 py-3 ${activeTab === 'proposals' ? 'bg-purple-100 text-purple-700 border-r-4 border-purple-500' : 'text-gray-600'}`} onClick={() => setActiveTab('proposals')}>
            <FileText className="w-5 h-5 mr-3" />
            <span className="font-medium">Proposals</span>
          </div>
          
          <div className={`flex items-center px-4 py-3 ${activeTab === 'matches' ? 'bg-purple-100 text-purple-700 border-r-4 border-purple-500' : 'text-gray-600'}`} onClick={() => setActiveTab('matches')}>
            <Award className="w-5 h-5 mr-3" />
            <span className="font-medium">Matches</span>
          </div>
        </nav>
        
        <div className="mt-auto p-4">
          <button 
            className="w-full py-2 bg-gradient-to-r from-purple-600 to-pink-600 text-white rounded-lg shadow-md font-medium flex items-center justify-center"
            onClick={() => setShowCreateModal(true)}
          >
            <Plus className="w-5 h-5 mr-2" />
            Create New DAO
          </button>
        </div>
      </div>
      
      {/* Main Content */}
      <div className="flex-1 overflow-y-auto">
        {/* Top Nav */}
        <div className="bg-white p-4 shadow-sm flex justify-between items-center">
          <div className="flex items-center">
            <div className="relative">
              <input 
                type="text" 
                placeholder="Search DAOs, proposals..."
                className="pl-10 pr-4 py-2 bg-gray-100 rounded-lg focus:outline-none focus:ring-2 focus:ring-purple-500 w-64"
              />
              <Search className="w-5 h-5 text-gray-400 absolute left-3 top-2.5" />
            </div>
          </div>
          
          <div className="flex items-center space-x-4">
            <button className="p-2 rounded-full bg-gray-100 relative">
              <Bell className="w-5 h-5 text-gray-600" />
              <span className="absolute top-0 right-0 w-2 h-2 bg-red-500 rounded-full"></span>
            </button>
            <div className="w-8 h-8 bg-purple-500 rounded-full"></div>
          </div>
        </div>
        
        {/* Dashboard Content */}
        {activeTab === 'dashboard' && (
          <div className="p-6">
            <div className="mb-8">
              <h2 className="text-2xl font-bold text-gray-800 mb-6">Welcome to Pollination Station</h2>
              
              <div className="bg-gradient-to-r from-purple-600 to-pink-600 rounded-xl p-6 text-white shadow-lg">
                <h3 className="text-xl font-semibold mb-2">Connect with Similar DAOs</h3>
                <p className="mb-4 opacity-90">Find DAOs that align with your mission and collaborate on impactful proposals.</p>
                <button className="bg-white text-purple-600 py-2 px-4 rounded-lg font-medium flex items-center">
                  Connect Me
                  <Zap className="ml-2 w-4 h-4" />
                </button>
              </div>
            </div>
            
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
              <div className="bg-white rounded-xl p-6 shadow-sm">
                <div className="flex justify-between items-center mb-4">
                  <h3 className="text-lg font-semibold text-gray-800">Top Matches</h3>
                  <button className="text-purple-600 text-sm font-medium">View All</button>
                </div>
                
                <div className="space-y-4">
                  {mockDAOs.slice(0, 2).map(dao => (
                    <div key={dao.id} className="flex items-center justify-between p-3 bg-gray-50 rounded-lg">
                      <div className="flex items-center">
                        <div className="w-10 h-10 bg-gradient-to-r from-blue-500 to-teal-500 rounded-full flex items-center justify-center text-white font-bold">
                          {dao.name.substring(0, 1)}
                        </div>
                        <div className="ml-3">
                          <h4 className="font-medium text-gray-800">{dao.name}</h4>
                          <p className="text-sm text-gray-500">{dao.description}</p>
                        </div>
                      </div>
                      <div className="flex items-center">
                        <span className="text-sm font-semibold bg-green-100 text-green-800 py-1 px-2 rounded-full">{dao.match}% Match</span>
                        <ArrowRight className="ml-2 w-4 h-4 text-gray-400" />
                      </div>
                    </div>
                  ))}
                </div>
              </div>
              
              <div className="bg-white rounded-xl p-6 shadow-sm">
                <div className="flex justify-between items-center mb-4">
                  <h3 className="text-lg font-semibold text-gray-800">Recent Proposals</h3>
                  <button className="text-purple-600 text-sm font-medium">View All</button>
                </div>
                
                <div className="space-y-4">
                  {mockProposals.map(proposal => (
                    <div key={proposal.id} className="p-3 bg-gray-50 rounded-lg">
                      <div className="flex justify-between mb-2">
                        <h4 className="font-medium text-gray-800">{proposal.title}</h4>
                        <span className={`text-xs font-semibold py-1 px-2 rounded-full ${proposal.status === 'Active' ? 'bg-blue-100 text-blue-800' : 'bg-yellow-100 text-yellow-800'}`}>
                          {proposal.status}
                        </span>
                      </div>
                      <div className="flex justify-between text-sm text-gray-500">
                        <span>From: {proposal.dao}</span>
                        <span>{proposal.created}</span>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            </div>
            
            <div className="bg-white rounded-xl p-6 shadow-sm">
              <div className="flex justify-between items-center mb-4">
                <h3 className="text-lg font-semibold text-gray-800">AI Collaboration Insights</h3>
                <span className="text-xs bg-purple-100 text-purple-800 py-1 px-2 rounded-full">Powered by AI</span>
              </div>
              
              <div className="p-4 border border-dashed border-purple-300 rounded-lg bg-purple-50 mb-4">
                <p className="text-gray-700">Based on your DAO profile, you could benefit from collaborating with <strong>ClimateDAO</strong> on joint funding initiatives for green technology.</p>
              </div>
              
              <div className="p-4 border border-dashed border-purple-300 rounded-lg bg-purple-50">
                <p className="text-gray-700">Consider creating a proposal for <strong>EduDAO</strong> to combine educational resources with your existing platform.</p>
              </div>
            </div>
          </div>
        )}
        
        {/* Matches Content */}
        {activeTab === 'matches' && (
          <div className="p-6">
            <div className="flex justify-between items-center mb-6">
              <h2 className="text-2xl font-bold text-gray-800">DAO Matches</h2>
              <button className="bg-purple-600 text-white py-2 px-4 rounded-lg font-medium flex items-center">
                <Zap className="mr-2 w-4 h-4" />
                Refresh Matches
              </button>
            </div>
            
            <div className="bg-white rounded-xl shadow-sm overflow-hidden">
              <table className="min-w-full divide-y divide-gray-200">
                <thead className="bg-gray-50">
                  <tr>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">DAO</th>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Description</th>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Members</th>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Proposals</th>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Match</th>
                    <th className="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Action</th>
                  </tr>
                </thead>
                <tbody className="bg-white divide-y divide-gray-200">
                  {mockDAOs.map(dao => (
                    <tr key={dao.id}>
                      <td className="px-6 py-4 whitespace-nowrap">
                        <div className="flex items-center">
                          <div className="w-10 h-10 bg-gradient-to-r from-blue-500 to-teal-500 rounded-full flex items-center justify-center text-white font-bold">
                            {dao.name.substring(0, 1)}
                          </div>
                          <div className="ml-3">
                            <p className="text-sm font-medium text-gray-900">{dao.name}</p>
                          </div>
                        </div>
                      </td>
                      <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">{dao.description}</td>
                      <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">{dao.members}</td>
                      <td className="px-6 py-4 whitespace-nowrap text-sm text-gray-500">{dao.proposals}</td>
                      <td className="px-6 py-4 whitespace-nowrap">
                        <span className="text-sm font-semibold bg-green-100 text-green-800 py-1 px-2 rounded-full">{dao.match}% Match</span>
                      </td>
                      <td className="px-6 py-4 whitespace-nowrap text-sm font-medium">
                        <button className="text-purple-600 hover:text-purple-900">Create Proposal</button>
                      </td>
                    </tr>
                  ))}
                </tbody>
              </table>
            </div>
          </div>
        )}
      </div>
      
      {/* Create DAO Modal */}
      {showCreateModal && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4">
          <div className="bg-white rounded-xl shadow-xl max-w-md w-full p-6">
            <h2 className="text-xl font-bold text-gray-800 mb-4">Create a New DAO</h2>
            
            <div className="space-y-4 mb-6">
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">DAO Name</label>
                <input type="text" className="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500" placeholder="Enter DAO name" />
              </div>
              
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">Description</label>
                <textarea className="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500" placeholder="What is your DAO's mission?" rows="3"></textarea>
              </div>
              
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">Focus Areas (select up to 3)</label>
                <div className="flex flex-wrap gap-2">
                  {["Climate", "Education", "Technology", "Art", "Finance", "Health", "Social Impact"].map(area => (
                    <div key={area} className="bg-gray-100 px-3 py-1 rounded-full text-sm cursor-pointer hover:bg-purple-100 hover:text-purple-700">
                      {area}
                    </div>
                  ))}
                </div>
              </div>
              
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">Needs</label>
                <textarea className="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-500" placeholder="What resources or collaborations is your DAO looking for?" rows="2"></textarea>
              </div>
            </div>
            
            <div className="flex justify-end space-x-3">
              <button className="px-4 py-2 text-gray-600 font-medium" onClick={() => setShowCreateModal(false)}>Cancel</button>
              <button className="px-4 py-2 bg-gradient-to-r from-purple-600 to-pink-600 text-white rounded-lg shadow-md font-medium">Create DAO</button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
};

export default PollinationStation;
```
